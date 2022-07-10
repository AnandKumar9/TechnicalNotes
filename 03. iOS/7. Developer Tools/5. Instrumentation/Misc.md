##### WWDC videos

WWDC 2021: Analyze HTTP traffic in Instruments <br>
WWDC 2019: Getting Started with Instruments <br>
WWDC 2019: Modeling in Custom Instruments <br>

WWDC 2018: Creating Custom Instruments <br>
WWDC 2018: Measuring Performance Using Logging <br>

WWDC 2015: Optimizing Swift Performance <br>

WWDC 2020: Diagnose performance issues with Xcode organizer <br>
WWDC 2018: Advanced Debugging with Xcode and LLDB <br>
WWDC 2018: iOS Memory Deep Dive <br>

--------

Lib vs framework
Concurrency notes
SPM notes

SPM EASE implementation
Xcodegen

Instrumentation
JavaScript

Building EASE web
Splunk
Safari and Web technologies
Server side code
Server side Swift/Xcode cloud
ML basics, CoreML, UI frameworks

--------

```
static let log = OSLog(subsystem: "com.package", category: "Behavior")
static let signpostID = OSSignpostID(log: AppDelegate.log, object: self as AnyObject)

os_signpost(.begin, log: AppDelegate.log, name: "event-tracking", signpostID: AppDelegate.signpostID, "size: %llu", before)
os_signpost(.end, log: AppDelegate.log, name: "event-tracking", signpostID: AppDelegate.signpostID, "size: %llu", after)
```
package.id
title.title

package.os-signpost-interval-schema.id
package.os-signpost-interval-schema.title

package.os-signpost-interval-schema.subsystem
package.os-signpost-interval-schema.category
package.os-signpost-interval-schema.name

CLIPS is a language Apple used for data processing in Instruments

column
expression’ tag contains CLIPS expression
create-table
graph

----

Reference documentation - https://help.apple.com/instruments/developer/mac/10.0/#/dev14811197

In Instruments UI (from a developer's perspective), there are two standardized components - the `Standard UI` and the `Analysis Core`. Think of the former as the front-end and the back-end as the database. The two are optimized to work on time series data. In a custom instrument essentially a custom configuration is beging specified for both of them.

In the UI, the top part is called `Graph view` (or `Track view`) and the bottom part is called `Detail view`. Each graph can have multiple `lanes`.

Every lane is bound to a certain table in the `Analysis Core`.


The `schema` defines a table's columns and the names, types, etc,. The Analysis Core data types are defined by a very rich typing system called an `engineering type` and that both tells us how to store the data and also how to visualize it and analyze it in the Standard UI.

`Attributes` define the table contents using key value pairs.

09:33
New Xcode Project, select macOS platform, and Instruments Package.


<import-schema>tick</import-schema>

----

