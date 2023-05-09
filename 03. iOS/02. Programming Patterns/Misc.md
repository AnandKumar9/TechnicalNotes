#### Dependency injection (DI)

It is nothing but offloading some of the work that an instance(class/struct/enum, etc.) could have done itself. Imagine the instance has a property and its actually well capable of determining its value all by itself (by calling some other singleton, etc.). I think its a sane thing to keep it this way, why ask someone else to do something for you that you can do yourself. But DI says not to do this.

As per DI, the instance should not find out the value itself but instead let it be assignable to the instance. It can be assigned as a property or even be a part of the initializer (which is still better) or can just be later passed in a method call (in which case the dependency is usually not a property).

What this apparently helps with is that "it separates responsibilities, an instance need not worry about doing too much", reduces coupling (probably too much of logic coupled together in a single instance), and (most importantly) improves testability. Improving testability still makes sense to me as then if the dependency is a sufficiently cumbersome thing then the dependency can just be mocked in a unit test class.

Its also very common to have the dependency property declared not as concrete type but as one conforming to a protocol. This is what in fact allows a mock conforming instance to be injected to the dependency in a test class.

[Link](https://cocoacasts.com/nuts-and-bolts-of-dependency-injection-in-swift/)

#### Wrapping Analytics API

Events are of certain types - `state`, `action`, termination, etc. Also the events can have attributes or properties associated with them which is nothing but a dictionary of key value pairs.

Typically there is some singleton, etc. that has methods which let you fire these events. All the API code is glued inside this singleton and abstracted. This wrapper is in fact built on top of this singleton.

So one thing to keep in mind is that whatever wrapper is built should allow type safety (i.e. consumers should not have to type hard coded event names), make the syntax as simple as possible for callers, and should allow unit testing. The unit testing can be done for correct values for event name, attributes, etc. and also for the fact that the view controllers are indeed firing the correct events. How much of unit testing makes sense though is for you to decide.

First up encapsulate the event in a struct.

```
struct AnalyticsEvent {    
    let name: String
    let type: AnalyticsEventType
    let properties: [String:String]
}

enum AnalyticsEventType: Int {
    case state
    case action
}
```

And then define instances of this struct for various events. There can even be an enum where all the events for a single feature are clubbed together.

```
enum SampleFeatureEvent: AnalyticsEventLogging {

    case event1
    case event2(properties: [String: String])

    var analyticsEvent: AnalyticsEvent {        
        switch self {            
        case .event1:
            return AnalyticsEvent(name: "event1", type: .state, properties: [:])
        case .event2(let properties):
            return AnalyticsEvent(name: "event2", type: .action, properties: properties)

        }
    }
}
```
And now unit testing can be performed on various cases of this enum.

Sometimes the wrapper can also be an enum instead of a struct (I think the struct approach is clearer though).

```
enum Event {
    case event1
    case event2(name: String, attribute1: String)
}

extension Event {
    var data: (name: String, metadata: [String:String]) {
        switch self {
        case .event1:
            return (name: "event1", metadata: [:])
        case .event2(let name, let attribute1):
            return (name: "event2", metadata: ["name": name, "attribute1": attribute1)
        }
    }
}
```

So at the place that these events need to be fired (say in view controllers), these events can be fetched and then dispatched to the Analytics singleton. Actually this analytics manager should be a 'Dependency Injection' enabling property so that in test targets it can be set to a mock analytics manager. This would even let you test if a view controller is indeed dispatching all the necessary events.

> Swift talk 83 (Wrapping analytics API) explains a lot of it.
