## 1.3.1
* replace vulnerable log4j 1.x logging library with logback
* bump dependencies

## 1.3.0
* when a requests [verification](https://github.com/jadler-mocking/jadler/blob/662704e1d5521972d4b0cf0f596e1c3dae68314f/jadler-core/src/main/java/net/jadler/Jadler.java#L756) fails the exact reason (a list of matching/clashing predicates for each request received so far) is logged on the INFO level
* the Jadler facade and the jUnit [rule](https://github.com/jadler-mocking/jadler/blob/662704e1d5521972d4b0cf0f596e1c3dae68314f/jadler-junit/src/main/java/net/jadler/junit/rule/JadlerRule.java) now provide the same defaults configuration options (response status, content type, encoding and headers defaults and the requests recording settings)
* a [reset method](https://github.com/jadler-mocking/jadler/blob/662704e1d5521972d4b0cf0f596e1c3dae68314f/jadler-core/src/main/java/net/jadler/Jadler.java#L723) added to the `Jadler` facade
* bugfix: in Jadler `1.2.0` two completely identical received requests are counted as one during a verification
* the version of `commons-collections` raised to `3.2.2` due to a [security vulnerability](https://commons.apache.org/proper/commons-collections/security-reports.html)

## 1.2.0
* experimental implementation of a stub server using [com.sun.net.httpserver](https://docs.oracle.com/javase/6/docs/jre/api/net/httpserver/spec/com/sun/net/httpserver/HttpServer.html) added as a new Jadler module `jadler-jdk`
* the Jetty (default) stub server implementation now sends the Date header in every response as requested in the [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.18)

## 1.1.2
* a bug preventing usage of the [net.jadler.Jadler](https://github.com/jadler-mocking/jadler/blob/f2197df3efa1e49e8cb6def08fd8a9a97e826523/jadler-core/src/main/java/net/jadler/Jadler.java) facade in conjunction with a jUnit test with a defined timeout value [fixed](https://github.com/jadler-mocking/jadler/blob/f2197df3efa1e49e8cb6def08fd8a9a97e826523/jadler-core/src/main/java/net/jadler/Jadler.java#L534).
* requests recording (for verification purpose) can now be turned off via a new configuration option [net.jadler.Jadler.OngoingConfiguration#skipsRequestsRecording](https://github.com/jadler-mocking/jadler/blob/352e85badd090cd3be00c8a28a69b69401e01951/jadler-core/src/main/java/net/jadler/Jadler.java#L735)
* Jadler can be built in JDK8 using Maven (proper doclint settings added for the javadoc plugin)

## 1.1.1
* [jadler-junit](https://github.com/jadler-mocking/jadler/blob/42a429ca31ae12c36ed8faf90014c91fa7a1e3c8/jadler-junit/pom.xml) artifact added, contains specific support for jUnit testing
* [net.jadler.junit.rule.JadlerRule](https://github.com/jadler-mocking/jadler/blob/42a429ca31ae12c36ed8faf90014c91fa7a1e3c8/jadler-junit/src/main/java/net/jadler/junit/rule/JadlerRule.java) jUnit rule added for easy Jadler lifecycle management

## 1.1.0
* stub http responses can now be defined dynamically using the [net.jadler.stubbing.Responder](https://github.com/jadler-mocking/jadler/blob/0dff7a0c8cbfd07d5e3f54a5f87f94e1ede021bc/jadler-core/src/main/java/net/jadler/stubbing/Responder.java) interface via the new [net.jadler.stubbing.RequestStubbing#respondUsing(Responder)](https://github.com/jadler-mocking/jadler/blob/0dff7a0c8cbfd07d5e3f54a5f87f94e1ede021bc/jadler-core/src/main/java/net/jadler/stubbing/RequestStubbing.java#L30) method
* a  [reset method](https://github.com/jadler-mocking/jadler/blob/0dff7a0c8cbfd07d5e3f54a5f87f94e1ede021bc/jadler-core/src/main/java/net/jadler/JadlerMocker.java#L356) added for the [net.jadler.JadlerMocker](https://github.com/jadler-mocking/jadler/blob/0dff7a0c8cbfd07d5e3f54a5f87f94e1ede021bc/jadler-core/src/main/java/net/jadler/JadlerMocker.java) class

## 1.0.0
* first stable version
* http mocking (verification) implemented: [net.jadler.Jadler#verifyThatRequest()] (https://github.com/jadler-mocking/jadler/blob/6b5338c8dc6ad64dce71aa4c8e73a424bfd869f6/jadler-core/src/main/java/net/jadler/Jadler.java#L533)
* methods for matching a request by its path renamed from `havingURI` (`havingURIEqualTo`) to more accurate `havingPath` (`havingPathEqualTo`): [net.jadler.RequestMatching#havingPathEqualTo(String)] (https://github.com/jadler-mocking/jadler/blob/6b5338c8dc6ad64dce71aa4c8e73a424bfd869f6/jadler-core/src/main/java/net/jadler/RequestMatching.java#L80)
* the method for setting a stub response delay renamed from `withTimeout` to more accurate `withDelay`: [net.jadler.stubbing.ResponseStubbing#withDelay(long, TimeUnit)] (https://github.com/jadler-mocking/jadler/blob/6b5338c8dc6ad64dce71aa4c8e73a424bfd869f6/jadler-core/src/main/java/net/jadler/stubbing/ResponseStubbing.java#L122)
* a `JadlerMocker` instance can now be disposed using a `close` method instead of a `stop` method. Once Jadler is switched to Java 7 `AutoCloseable` will be retrofitted easily: [net.jadler.JadlerMocker#close()](https://github.com/jadler-mocking/jadler/blob/6b5338c8dc6ad64dce71aa4c8e73a424bfd869f6/jadler-core/src/main/java/net/jadler/JadlerMocker.java#L138)
* a custom request abstraction introduced and used across the whole library: [net.jadler.Request](https://github.com/jadler-mocking/jadler/blob/6b5338c8dc6ad64dce71aa4c8e73a424bfd869f6/jadler-core/src/main/java/net/jadler/Request.java)

## 0.9.5
* first public version
* http stubbing implemented
