---
layout: post
title: "Notes from Lonestar Elixir Conference (2020)"
date: 2020-01-13 20:08 -0600
---

Great conference. Great community. 10/10 would attend again.

## TBA - [Anna Neyzburg](https://twitter.com/ANeyzb)

- Community affects the software we build
- > "So much about building software—more than anyone wants to admit—is etiquette" - [Paul Ford](https://www.wired.com/story/why-we-love-tech-defense-difficult-industry/)
- [Thinking, Fast and Slow](https://www.goodreads.com/book/show/11468377-thinking-fast-and-slow) - Daniel Kahneman
- Loss > Gains
- People feel empowered to make decisions when they feel confident
- Status Distance === Bias
- [Fluency Hueristic](https://medium.com/gravityblog/9-fluency-heuristic-43283333918a) = better it sounds, more likely it is to "win" (aka the best ideas don't always win)
  [![Fluency Hueristic](/assets/images/lonestar-elixir-conf-2020/01.jpg)](https://medium.com/gravityblog/9-fluency-heuristic-43283333918a)
- Clear expectations of behavior
- Language matters (be careful what you say)
- [ElixirBridge](http://elixirbridge.org/docs/) - outreach for underrepresented people in tech
- Used [Spectacle](https://formidable.com/open-source/spectacle/) for slides
- Everyone has limited knowledge, but unlimited potential
  [![Everyone has limited knowledge, but unlimited potential](/assets/images/lonestar-elixir-conf-2020/02.jpg)](https://twitter.com/eugico/status/1233052570723246081)

## All Aboard the Stateful Train - [Eric Oestrich](https://twitter.com/EricOestrich)

- [ExVenture](https://exventure.org/) - MUD server (_very_ stateful)
- [Grapevine](https://grapevine.haus/)- MUD Community (think steam for Elixir)
- Stateful = less database, more OTP
- Using GenServers as the basic building blocks
- :ets for caching (rather than Redis) and occasionally write state to a database for re-hydration (_when_ things go wrong; still use the DB as the source of truth)
- [Kalevale](https://github.com/oestrich/kalevala) (new ExVenture)
- [Designing Elixir Systems with OTP](https://pragprog.com/book/jgotp/designing-elixir-systems-with-otp)

## Getting the Frog Out of the Well - [Zach Thomas](https://twitter.com/ZachDCThom)

- more things suck, less productive you become
- > "Sure, we could talk about aesthetic resonance a bit if you prefer that?" - Zach

## Tests Friend or Foe? Chain or Cable? - [Mark Windholtz](https://twitter.com/windholtz)

- Spoiler: Friend
- Cables: connect two far away points (UI to DB; ~integration tests)
- Chain (or chain of links): unit tests for business logic that test _every_ conditional branch (think chain mail, rather than linear linkage)
- [A Set of Unit Testing Rules - Michael Feathers](https://www.artima.com/weblogs/viewpost.jsp?thread=126923) (basically test pure functions)
- [Mocks and explicit contracts - José Valim](http://blog.plataformatec.com.br/2015/10/mocks-and-explicit-contracts/)

## From Bootcamp To Elixir Contracts: A Road Less Traveled - [Melvin Cedeno](https://twitter.com/TheCraftedGem)

- [Council on Integrity in Results Reporting (CIRR)](https://cirr.org/) - reports on bootcamps
- Use [OODA loop](https://en.wikipedia.org/wiki/OODA_loop) for learning
- [Turing School](https://turing.io/)
- [Stoic Readings (app)](https://f-droid.org/en/packages/app.reading.stoic.stoicreading/)
- Practice with [Advent of Code](https://adventofcode.com/)
- Jobs:
  - [Elixir Slack](https://elixir-slackin.herokuapp.com/)
  - [Elixir Forum](https://elixirforum.com/)
  - [AngelList](https://angel.co/)
  - [Plataformatec](http://plataformatec.com.br/elixir-radar/jobs)

## Responsible Resources - [Justin Schneck](https://twitter.com/mobileoverlord)

- > "We are just statistics, born to consume resources." - [Horace](https://www.goodreads.com/quotes/7500446-we-are-just-statistics-born-to-consume-resources)
- Docker will consume the world if you let it
  [![Docker will consume the world if you let it](/assets/images/lonestar-elixir-conf-2020/03.jpg)](https://twitter.com/ANeyzb/status/1233123058740813825)
- [Clean your room, clean your code, you ain't gunna need it](https://martinfowler.com/bliki/Yagni.html)
- Wireless communication:
  - [LoRaWAN (**Lo**ng **Ra**nge)](https://en.wikipedia.org/wiki/LoRa#LoRaWAN)
  - [Wi-Fi Mesh](https://en.wikipedia.org/wiki/Wireless_mesh_network)
  - [RF](https://en.wikipedia.org/wiki/Radio_frequency)
- [VintageNet](https://github.com/nerves-networking/vintage_net) - new Nerves networking library

## OpenTelemetry - [Greg Mefford](https://twitter.com/ferggo)

[![Standards](https://imgs.xkcd.com/comics/standards.png)](https://xkcd.com/927/)

- [OpenTelemetry](https://opentelemetry.io/) - standards for traces and metrics
- [reacon_trace](https://ferd.github.io/recon/recon_trace.html)

## The Grand Bank of Jon Jon - [Jon Carstens](https://twitter.com/JonCarstens)

[![The Grand Bank of Jon Jon](/assets/images/lonestar-elixir-conf-2020/05.jpg)](https://twitter.com/JonCarstens/status/1233427328841191424)

## Physically-Based Rendering Using Elixir - [Jason Stewart](https://medium.com/@jason.r.stewart)

- Can we make a 3D rendering engine in Elixir? Yes. Should we? Maybe.
- [raytracer-ex](https://github.com/jrstewart/raytracer-ex)
- Results: slow, but faster than expected

## Joe - [Bruce Tate](https://twitter.com/redrapids) and [Brian Troutwine](https://twitter.com/bltroutwine)

- [Normal Accidents - Charles Perrow](https://www.goodreads.com/book/show/192408.Normal_Accidents)
- Read [Joe's writings](https://joearms.github.io/#Index)
  - Check out the [Universal Server](https://joearms.github.io/#2013-11-21%20My%20favorite%20Erlang%20Program) (aka Joe's favorite Erlang program)
  - [Making reliable distributed systems in the presence of software errors](https://erlang.org/download/armstrong_thesis_2003.pdf) (Joe's thesis)

## Yeah... but should we? - [Randall Thomas](https://twitter.com/daksis)

- Check out [The Register](https://www.theregister.co.uk/)
- [Facial recognition algorithms struggle to "see" black people](https://www.ted.com/talks/joy_buolamwini_how_i_m_fighting_bias_in_algorithms/)
- [IBM and the Holocaust](https://en.wikipedia.org/wiki/IBM_and_the_Holocaust)
- We don't need malicious motivation to create systems that enable entities to cause harm. Something as simple as "profit" is reason enough.

## Browser Automation Testing: Best practices - Best tools - [Vanessa Lee](https://twitter.com/girlsleuthcom)

- Remember to...
  1. Verify dependencies
  2. Expect unknown unknowns
  3. Expect failures
- [Wallaby](https://hexdocs.pm/wallaby/Wallaby.html)
- [Hound](https://hexdocs.pm/hound/readme.html)

## Taming :ets - [Mike Binns](https://twitter.com/1stAvenger)

- `(ArguementError)` - used for _so many errors_
- [ETS](https://github.com/TheFirstAvenger/ets) - an Elixir wrapper for `:ets`

## Nobody: Literally No One: Me: Let's Write CSS in Elixir! - [Ben Wheat](https://twitter.com/BeardyWheat)

- [Scenic](https://hexdocs.pm/scenic/welcome.html) - Elixir's graphic language
- [scenic_layout_o_matic](https://github.com/BWheatie/scenic_layout_o_matic)
- _Idea_: try using scenic rather than Electron for desktop apps

## Why You Should Use Nerves for Your Next (or First) Hardware Project - [Todd Resudek](https://twitter.com/sprsmpl)

- [drizzle](https://github.com/supersimple/drizzle)
- [breathe](https://github.com/supersimple/breathe)
- [Nerves](https://nerves-project.org/)

## Brook: Distrubuted event-driven library for Elixir - [Jeff Grunewald](https://github.com/jeffgrunewald)

- "The Microservice Actor" - the actor model gives microservices (almost) out of the box
- `GenServer.abcast/3` or `GenServer.multi_call/4`
- [Brook](https://github.com/bbalser/brook)
- Steps:

  1.  Event bus

      - pub/sub broadcasting
      - unified view (independent of any service)

  2.  Event contract

          - message structure (minimal and assertive)
          ```elixir

      %{
      type: string,
      author: string,
      created_at: pos_int,
      data: term(), # like an HTTP body
      forwarded: bool
      }

  ```
  3. Serialization
    - message log interface
    - non-BEAM system
    - storage
    - JSON
  4. View state
    - track and view what's needed and who's responsible
  ```

## Let's Make a Pizza! Batch Operations with Broadway - [Michael Crumm](https://twitter.com/mcrumm)

- [Broadway](https://hexdocs.pm/broadway/Broadway.html)
- Optimize with production server

## Telemetry: By the Numbers - [Samuel Mullen](https://twitter.com/samullen)

- [Telemetry](https://github.com/beam-telemetry/telemetry)

## [What I Learned About Code Reviews From Teaching 8th Grade Poetry](https://docs.google.com/presentation/d/12XFRkVjtUu9v8X5bkB5gumxtWSCFwGBfGPZnjE2HQNA/edit#slide=id.p) - [Andrew Ek](https://twitter.com/ektastrophe)

- Give people room to be wrong
- Practice, practice, practice
- Most changes only need 1-2 reviewers
- Prefer _small_ changes
- Leave fewer comments

## How I'm Becoming a Programmer - [Dave Thomas](https://twitter.com/pragdave/)

- > "There are no best practices" - Dave Thomas
- Goals:
  1. Happy doing what I'm doing
  2. Developing and learning (as a human)
  3. Changing the world for the better
     [![Dave's Three Goals](/assets/images/lonestar-elixir-conf-2020/06.jpg)](https://twitter.com/eugico/status/1233526488269496321)
- Happy
  - You have agency (change where you're working _or_ change where you're working)
- Growing
  - [A Five-Stage Model of the Mental Activities Involved in Directed Skill Acquisition - Dreyfus Brothers](https://apps.dtic.mil/dtic/tr/fulltext/u2/a084551.pdf)
    - It's the novice level that pays tomorrow's bills
  - Rule of three: if you see it 3 times in relatively close succession, check it out

---

## Random Conversations

- [Screaming Porgs](https://2019.cascadiajs.com/speakers/dominik-kundel)
- [Haskell.Prelude](https://www.nuget.org/packages/Haskell.Prelude/) (for C#)
- [Property-Based Testing with PropEr, Erlang, and Elixir](https://pragprog.com/book/fhproper/property-based-testing-with-proper-erlang-and-elixir)
- [Desiging Elixir Systems with OTP](https://pragprog.com/book/jgotp/designing-elixir-systems-with-otp)
- [Domain Modeling Made Functional](https://pragprog.com/book/swdddf/domain-modeling-made-functional) (F# and DDD)
- Use PID loop to manage temperature with potential nerves project
  - [pidex](https://github.com/elcritch/pidex) (probably this one)
  - [pid_controller](https://github.com/CraigCottingham/pid_controller)
- [Hitchhiker's guide to the BEAM](https://youtu.be/fctrWbgbJg0)
- [MobX State Tree](https://mobx-state-tree.js.org/intro/philosophy)
