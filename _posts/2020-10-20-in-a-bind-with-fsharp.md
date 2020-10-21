---
layout: post
title: In a Bind with F#
date: 2020-10-20 11:42 +0200
---

While going through the [F# exercism track](https://exercism.io/my/tracks/fsharp), I stumbled upon F#'s `bind` function.

One of my favorite things about Exercism is the ability to view other user's published solutions. In this case, the most starred solution for **Phone Number** by _alex123098_ had an interesting solution using `Result.bind` and `Result.map` ([check it out here](https://exercism.io/tracks/fsharp/exercises/phone-number/solutions/7a5d2cf04216475cab7ea251fd8289a9)). Thus begins our journey.

_Note: For a more in-depth post, please check out Scott Wlaschin's post on [Understanding bind](https://fsharpforfunandprofit.com/posts/elevated-world-2/)._

## "Unbound" Solution

My original solution wasn't the most _functional_ or the easiest to reason through. I really disliked it. I really wanted a ["railway oriented programming"](https://fsharpforfunandprofit.com/posts/recipe-part2/) way to attack this problem.

```fsharp
module PhoneNumber

open System

let clean (input: string) =
module PhoneNumber

open System

let clean (input: string) =
    let validPunctuation = [ '-'; '('; ')'; '.' ]

    let isInvalidPunctuation c =
        Char.IsPunctuation c
        && not (List.contains c validPunctuation)

    match input with
    | phone when phone |> String.exists Char.IsLetter -> Error "letters not permitted"
    | phone when phone |> String.exists isInvalidPunctuation -> Error "punctuations not permitted"
    | phone ->
        let removeCountryCode (phone: string) =
            if phone.Length = 11 then phone.[1..] else phone

        let filtered = phone |> String.filter Char.IsDigit
        let noCountryCode = filtered |> removeCountryCode

        match noCountryCode with
        | _ when filtered.Length = 11
                 && not (filtered.StartsWith('1')) -> Error "11 digits must start with 1"
        | _ when filtered.Length > 11 -> Error "more than 11 digits"
        | phone when phone.Length <> 10 -> Error "incorrect number of digits"
        | phone when phone.StartsWith('0') -> Error "area code cannot start with zero"
        | phone when phone.StartsWith('1') -> Error "area code cannot start with one"
        | phone when phone.[3] = '0' -> Error "exchange code cannot start with zero"
        | phone when phone.[3] = '1' -> Error "exchange code cannot start with one"
        | phone -> (uint64 >> Ok) phone
```

So with this "good enough" solution to parse a phone number in mind, let's look at what `bind` gives us.

## Binding the Solution

```fsharp
module PhoneNumber

open System

let private scrub (input: string) =
    let validPunctuation = [ '('; ')'; '-'; '.'; '+'; ' ' ]

    input
    |> String.filter (fun c -> not (List.contains c validPunctuation))

let private validateLength input =
    match String.length input with
    | length when length < 10 -> Error "incorrect number of digits"
    | length when length > 11 -> Error "more than 11 digits"
    | _ -> Ok input

let private validateCountryCode input =
    match String.length input with
    | 11 when input.[0] <> '1' -> Error "11 digits must start with 1"
    | 11 -> Ok input.[1..]
    | _ -> Ok input

let private validateNoLetters input =
    if String.exists Char.IsLetter input then Error "letters not permitted" else Ok input

let private validateNoPunctuation input =
    if String.exists Char.IsPunctuation input then Error "punctuations not permitted" else Ok input

let private validateAreaCode (input: string) =
    match input.[0] with
    | '0' -> Error "area code cannot start with zero"
    | '1' -> Error "area code cannot start with one"
    | _ -> Ok input

let private validateExchangeCode (input: string) =
    match input.[3] with
    | '0' -> Error "exchange code cannot start with zero"
    | '1' -> Error "exchange code cannot start with one"
    | _ -> Ok input

let clean (input: string): Result<uint64, string> =
    input
    |> scrub
    |> validateLength
    |> Result.bind validateCountryCode
    |> Result.bind validateNoLetters
    |> Result.bind validateNoPunctuation
    |> Result.bind validateAreaCode
    |> Result.bind validateExchangeCode
    |> Result.map uint64
```

Now we can read the `clean` function and understand what it does at each step. Let's take a closer look at the the signature of `validateLength` and `validateCountryCode`.

```fsharp
validateLength string -> Result<string, string>
validateCountryCode string -> Result<string, string>
```

Notice how `validateLength` returns `Result<string, string>`, yet it pipes into `validateCountryCode` which accepts a `string`.

🤯

So `Result.bind` effectively allows us to avoid having to write functions like

```fsharp
let divide (result: Result<int * int, string>): Result<int, string> =
    match result with
    | Ok (_, 0) -> Error "divisor cannot be zero"
    | Ok (dividend, divisor) -> Ok (dividend / divisor)
    | Error e -> Error e

let add1 (result: Result<int, string>): Result<int, string> =
  match result with
  | Ok number -> Ok (number + 1)
  | Error e -> Error e

Ok (10, 0) |> divide |> add1
// Error "divisor cannot be zero"
```

and instead write

```fsharp
let divide (numbers: int * int): Result<int, string> =
  match numbers with
  | (_, 0) -> Error "divisor cannot be zero"
  | (dividend, divisor) -> Ok (dividend / divisor)

let add1 (number: int): Result<int, string> =
  Ok (number + 1)

Ok (10, 0) |> Result.bind divide |> Result.bind add1
// Error "divisor cannot be zero"
```

While this is a simple example, hopefully it demonstrates how `bind` helps us simplify the internals of our functions without losing context.
