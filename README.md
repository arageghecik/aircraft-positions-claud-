# aircraft-positions-claud

### Event Driven Architecture (EDA)

it is equivalent webflux_redis, webflux_jpa_RDBAndNoSql,\
but it is massaging without webflux, it is massaging by claud technology\
and other new thing is rabbit message broker server

### how it works
this app concept is - Supplier -> consumer(planefinder ->rabbit->aircraft-positions) concept\
before this aircraft-positions(webflux_redis,webflux_jpa_RDBAndNoSql) requested to planefinder(tag:claud_strategy_without_kafka) for data, but naw planfinder is sending data to RabbitMQ and aircraft-positions pull from rabbit \
it is sanding data by his  Supplier<Iterable<Aircraft>> reportPositions() method every second(without @scheduler), which annotated @bean \
and in application.properties we set the direction where are sanding we data (appropriate the aircraft-positions getting data process)
  
#### WebSocket part
  
![WebSocket](https://user-images.githubusercontent.com/118361758/204624007-4b112159-25d6-4d37-b6b1-cbcdbbc9c035.png)

  its need some libs for cloud technology
  
 
  <dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-stream</artifactId>
	</dependency>
  <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-amqp</artifactId>
	</dependency>
	<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-stream-binder-rabbit</artifactId>
	</dependency>
