CoreML2, CreateML
Siri shortcuts
Metal improvements, Dependency viewer, Shader source code debugger
ARKit2, usdz file format
Password auto-fill across native apps and websites

UIKit apps on Mojave
Quick actions in Finder on Mojave
Dark mode in Mojave
Mojave will be the last macOS to support 32 bit apps

Swift 4.2
Xcode 10 multi cursor editing, parallel testing
Instruments extended to have custom tools and workflows
New logging api os_signpost

**********

Password management -

iOS Can create, store and auto-fill strong passwords. Auto-fill even works in native apps.
Syncs to all devices using iCloud. For the auto-fill to work in native app, the app has to be associated with domain and the fields should be labeled . This association automatically happens if you are using universal links.
Siri can pull up all passwords and show you the list in clear text (No separate app per se it seems).
OTP codes can automatically show up in keyboard suggestions. Needs any dev effort?

New password auto-fill extension for password management by third party vendors.

**********

Improved Xcode logging and instrumentation -

New logging api os_signpost.
Instruments extended to have custom tools and workflows.

os_log an already existing API that efficiently captures logs and trace points across the system.
os_signpost is a new api. It gives data in such a way that Instruments arrange, can be used for custom instruments visualization. Can do more things.

Already existing dev tools - Static analyzer, runtime issues(?), accessibility inspector, runtime sanitizers, localization tools, xctest, code coverage, crash logs, energy logs, view debugger, memory debugger, debug gauges, instruments

import os.log
import os.signpost

.begin, .end
.pointOfInterest

Creating custom Instruments package/templates.

**********

32 bit deprecation after Mojave -

High Sierra was the last macOS to fully support 32 bit apps without compromises.
Mojave will be the last macOS to support 32 bit apps (so makes compromises even for supporting?).

Some 32 bit frameworks will hence be removed in next OS. This includes QT and Carbon HHTLB frameworks.

Increased user consent requirement for many more mac hardware resources and user data.

Notary service which accounts for all versions of macOS apps.

**********

UX enhancements in Mojave -

Quick actions

Finder quick actions now will have actions (CTAs) in preview pane itself. (So does it show up in quick look pane or the Finder tab, looks like latter) Custom actions through app extensions.

In automator, shell scripts, apple scripts and automator actions can be combined to create action bundles. And even these custom action bundles can show up in Finder (for specific file types?).

**********

UIKit apps on Mac -

The stack underlying both UIKit and AppKit were pretty similar (Media, CoreOS, CoreServices, etc.). They are hence being unified gradually. So UIKit apps will run on Mojave! (slowly being rolled of)

Shows in iPad layout?
Can go full screen

**********

Dark mode on Mojave -

Apps have to opt-in for supporting dark mode, there is slight change in some of the macOS API.

Assets catalog will now have another option to include dark variants for all resources.

**********

Xcode improvements -

Xcode 10. Lot more source control change highlight in source control change bar. Even actionable.
Multi-cursor editing (Ctrl + Shift and click at the start of all the places you want to edit).
Code folding ribbon restored.

Catalog colors have already been there.

Xcode now also integrates with BitBucket and Gitlab.

Faster start up and more precise value output by LLDB.
Device symbols downloaded 5 times faster.

Testing improvements.
automatically include new tests (what is that?)
randomize test order (was it not random already?)
execute in parallel (ok so it means multiple suites can run together, even UI tests!)

New build system that was launched sometime back. Its faster.

**********

Swift 4.2 -

Lot more features. Future enum cases, conditional conformance, etc.
Binary size will be smaller.  But how does this depend upon the programming language.

Xcode playgrounds can now execute new lines of code without having to restart the playground (no need to stop an ongoing execution and run again.)

Swift 5 releasing in early 2019. Will focus on binary (ABI?) compatibility and more.

**********

Machine Learning -

CoreML2, CreateML launched.
People segmentation possible. Extract people or object from images, substitute with something else.
NLP - Automatic identification of language (English, Spanish, etc.)
More semantic understanding of sentences.

CoreML has been adopted by every major ML training framework (IBM Watson, Turi, etc.) over the past year.

CoreML2 models will be faster, smaller and more customizable.

CreateML is a new framework to train models.

**********

Siri shortcuts -

No need to specify the app name.

New SiriKit Intents API

Custom voice trigger and responses. Targeted predictions of when the shortcut will be useful to user.

**********

Metal improvements -

Apple-designed GPU optimized for Metal2. OpenGL and OpenCL will be deprecated.

New Metal tools - Metal dependency viewer, GPU source code shader debugger
Existing Metal tools - C++ shading language, GPU performance counter, Visual API debugger, Metal system trace

GPU driven command encoding in Mojave.

**********

AR improvements -

New mobile AR format called usdz. Optimized for mobile devices. Natively supported in SceneKit.
ARKit2 introduced. Has improved face tracking, environment texturing. 3D image detection and tracking. Environment map sharing with other devices also possible.
