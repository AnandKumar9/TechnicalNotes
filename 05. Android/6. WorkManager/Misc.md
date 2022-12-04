Worker <br>
WorkRequest <br>
WorkManager <br>

Bootcamp Tutorial [link](https://developer.android.com/codelabs/android-workmanager?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-6-pathway-1%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fandroid-workmanager#1) <br>
Guide to background precessing ([link](https://developer.android.com/guide/background/)) <br>

#### What is WorkManager

`WorkManager` is one way to perform deferrable background work in Android. Its backwards compatible and is guaranteed to be executed.

Its a part of Android Jetpack. Opportunistic execution means that WorkManager will do your background work as soon as it can. Guaranteed execution means that WorkManager will take care of the logic to start your work under a variety of situations, even if you navigate away from your app.


It offers plenty of things.
- Support for both asynchronous one-off and periodic tasks.
- Support for constraints such as network conditions, storage space, and charging status.
- Chaining of complex work requests, including running work in parallel.
- Output from one work request used as input for the next.
- Handling API level compatibility back to API level 14 (see note).
- Working with or without Google Play services.
- Following system health best practices.
- LiveData support to easily display work request state in UI.

Internally, it sits on top of a few APIs such as `JobScheduler` and `AlarmManager` and automatically picks the right APIs to use, based on conditions like the user's device API level.

Some examples of tasks that are a good use of WorkManager.
- Uploading logs
- Applying filters to images and saving the image
- Periodically syncing local data with the network

> While `WorkManager` offers guaranteed execution it is not a catch-all for running every task off of the main thread.

#### Gradle dependencies

app/build.gradle
```
dependencies {
    implementation "androidx.work:work-runtime-ktx:$versions.work"
}
```

build.gradle
```
versions.work = "2.7.1"
```

#### Basics

`Worker` - This is where you put the code for the actual work you want to perform in the background. You'll extend this class and override the doWork() method.

`WorkRequest` - This represents a request to do some work. You'll pass in your Worker as part of creating your WorkRequest. When making the WorkRequest you can also specify things like Constraints on when the Worker should run.

`WorkManager` - This class actually schedules your WorkRequest and makes it run. It schedules WorkRequests in a way that spreads out the load on system resources, while honoring the constraints you specify.

There are two types of `WorkRequests`. <br>
`OneTimeWorkRequest` - A `WorkRequest` that will only execute once. <br>
`PeriodicWorkRequest` - A WorkRequest that will repeat on a cycle. <br>

`cancelUniqueWork()` can be used to cancel a work.

`Constraints.Builder()` can be used to add constraints (for example device must be charging, etc.) as needed.
