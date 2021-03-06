[![Build Status](https://travis-ci.org/LoyolaChicagoCode/clickcounter-spray-scala.svg)](https://travis-ci.org/LoyolaChicagoCode/clickcounter-spray-scala)
[![codecov](https://codecov.io/gh/LoyolaChicagoCode/clickcounter-spray-scala/branch/master/graph/badge.svg)](https://codecov.io/gh/LoyolaChicagoCode/clickcounter-spray-scala)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/1ffc88abb7ea4e768e564abd3fe5b498)](https://www.codacy.com/app/laufer/clickcounter-spray-scala?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=LoyolaChicagoCode/clickcounter-spray-scala&amp;utm_campaign=Badge_Grade)

[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/LoyolaChicagoCode/clickcounter-spray-scala.svg)](http://isitmaintained.com/project/LoyolaChicagoCode/clickcounter-spray-scala "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/LoyolaChicagoCode/clickcounter-spray-scala.svg)](http://isitmaintained.com/project/LoyolaChicagoCode/clickcounter-spray-scala "Percentage of issues still open")

# RESTful Click Counter Service

This is a RESTful click counter service implemented in Scala
using [spray](http://spray.io) and [Redis](http://redis.io)
and [documented on Apiary](http://docs.clickcounter.apiary.io).

It is intended as an end-to-end example for teaching and exemplar for
research explorations in the area of collaborative distributed/mobile
applications. As such, it is based on a very simple domain model but
demonstrating the full depth of the solution stack.

An
[Android client app](https://github.com/LoyolaChicagoCode/clickcounter-android-rxscala-http)
for this service is now available.

# Learning Objectives

An understanding of

- RESTful web services
- Stateless API layer
- Stateful resources
- Persistent storage
- Server-side concurrency and scalability, in particular, asynchronous,
  nonblocking end-to-end request processing using Akka futures
- Hosted cloud-based continuous integration and deployment
  (see status badges at the top)

# Documentation

The service API is [documented on Apiary](http://docs.clickcounter.apiary.io),
which automatically generates a hosted mock server based on Apiary's
extended markdown documentation.

# Implementation

The service is written in Scala and leverages these libraries:

- [spray-can](http://spray.io/documentation/1.2.2/spray-can),
  an lightweight, embedded, asynchronous HTTP server.
- [spray-routing](http://spray.io/documentation/1.2.2/spray-routing),
  a high-level DSL for writing defining RESTful APIs.
- [scredis](https://github.com/Livestream/scredis),
  a high-quality, well-documented, non-blocking [Redis](http://redis.io) client
  with support for publish-subscribe.

# Testing

The tests use these libraries:

- [spray-testkit](http://spray.io/documentation/1.2.2/spray-testkit/),
  a DSL for out-of-container testing of RESTful API routes.
- [Dispatch](http://dispatch.databinder.net),
  an HTTP client for in-container testing of deployed services.
  *The in-container tests can be invoked on the mock server,
  a local service instance, or the instance running on Heroku.*
- [specs2](http://etorreborre.github.io/specs2),
  a library for writing software specification that
  includes nice matchers (especially for JSON).

# Development

For efficient development of spray web services, we highly recommend
[sbt-revolver](https://github.com/spray/sbt-revolver). Start the service
locally like so

    sbt
    > ~re-start

and any changes to the sources result in hot redeployment.

Before deploying to Heroku, we recommend verifying that the service
runs locally in the environment it will have on Heroku. This approach is
[described here](https://devcenter.heroku.com/articles/graphstory#local-setup)
for an unrelated addon but applies generally.

# Deployment

This serves as an exemplar of a spray service backed
by Redis and deployable to [Heroku](http://www.heroku.com),
which [directly supports Scala with sbt](https://devcenter.heroku.com/articles/scala-support).
The service uses the Heroku [Rediscloud](https://addons.heroku.com/rediscloud) addon.

A sample instance is running
[here](http://laufer-clickcounter.herokuapp.com). It tends to go above
the Redis Labs connection limit, however, and will stop working
temporarily. You are encouraged to host your own service instance.

# References

[This short video](https://www.youtube.com/watch?v=b2F-DItXtZs)
([transcript](http://www.mongodb-is-web-scale.com))
includes a very brief discussion of the advantages of Redis,
among other related topics.
