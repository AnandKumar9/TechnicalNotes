##### Using Targets to have multiple versions -

Duplicate an existing target, go to build settings of both the targets and add unique preprocessor macros in all the configurations to uniquely distinguish between the targets. Then in the code, check the current target by using `#ifdef` and put the appropriate code in the if blocks.

```
#ifdef LITE_VERSION
     NSLog(@"****Lite version****");
#endif

#ifdef COMPLETE_VERSION
     NSLog(@"****Complete version****");
#endif
```



-----------
