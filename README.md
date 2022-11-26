# aircraft-positions-claud

it is equivalent webflux_redis, webflux_jpa_RDBAndNoSql,\
but it is massaging without webflux, it is massaging by claud technology\
and other new thing is rabbit message broker server

<h3>how it works</h3>
this app concept is - Supplier -> consumer(planefinder ->rabbit->aircraft-positions) concept\
before this aircraft-positions(webflux_redis,webflux_jpa_RDBAndNoSql) requested to planefinder(tag:claud_strategy_without_kafka) for data, but naw planfinder is sending data to RabbitMQ and aircraft-positions pull from rabbit \
it is sanding data by his  Supplier<Iterable<Aircraft>> reportPositions() method every second(without @scheduler), which annotated @bean\
and in application.properties we set the direction where are sanding we data (appropriate the aircraft-positions getting data process)