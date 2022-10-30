`Gradle` is the automated build system used by Android Studio.

There are several gradle scripts (i.e. `.gradle` files) in the project. ([Reference](https://developer.android.com/studio/build#kts))

![](assets/Misc-a6d3f88b.png)

When the gradle script is changed, a new sync is usually needed for the project. A message is shown for that.

##### Enabling various features

For enabling `view bindings`, the `build.gradle (Module:..)` file needs to be updated with this (and not the `build.gradle (Project:..)`) file.

```
buildFeatures {
    viewBinding = true
}
```
