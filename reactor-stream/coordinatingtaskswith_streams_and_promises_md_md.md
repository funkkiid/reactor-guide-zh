
## Coordinating tasks with Streams and Promises

![Figure 9. How Doge can use Reactor-Stream](http://projectreactor.io/docs/reference/images/streams-overview.png)
**Figure 9. How Doge can use Reactor-Stream**

**Reactor Streams** has the following artifacts:

* Stream and its direct implementations
 * Contains reactive extensions and other composition API
* Promise with a specific A+ flavored API
 * Can be transformed back to Stream with Promise.stream()
* Static Factories, the one-stop-shops to create related components
 * Streams for Stream creation from well-defined data sources (Iterable, nothing, Future, Publisher…)
 * BiStreams for key-value Stream<Tuple2> processing (reduceByKey…)
 * IOStreams for Persisting and Decoding Streams
 * Promises for single-data-only Promise
* Action and its direct implementations of every operation provided by the Stream following the Reactive Streams Processor specification
 * Not created directly, but with the Stream API (Stream.map() → MapAction, Stream.filter() → FilterAction…)
* Broadcaster, a specific kind of Action exposing onXXXX interfaces for dynamic data dispatch
 * Unlike Core Processors, they will usually not bother with buffering data if there is no subscriber attached
 * However the BehaviorBroadcaster can replay the latest signal to new Subscribers

> *Do not confuse reactor.rx.Stream with the new JDK 8 java.util.stream.Stream. The latter does not offer a Reactive Streams based API nor Reactive Extensions. However, the JDK 8 Stream API is quite complete when used with primitive types and Collections. In fact it’s quite interesting for JDK 8 enabled applications to mix both JDK and Reactive Streams.*