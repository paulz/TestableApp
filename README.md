# TestableApp
Sample project to show Xcode 9.4 fails to link Logic Test target

# Summary:

Previously we were able to create LOGIC tests in Xcode as opposed to APPLICATION tests. Xcode 9.4 fails to link logic tests with this message:

```
Undefined symbols for architecture x86_64:
  "type metadata accessor for <ClassUnderTest>", referenced from:
      <TestTarget.TestClass>.setUp() -> () in GoodAppTestsWithoutHost.o
      type metadata accessor for <ClassUnderTest>.Type in <TestTarget>.o
ld: symbol(s) not found for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```

# Steps to Reproduce:

  1. Open `TestableApp/GoodApp.xcodeproj` in Xcode 9.4
  3. Select GoodAppTests scheme and press Cmd-U to test Application Tests with host works fine.
  3. Select GoodAppTestsWithoutHost scheme and a iOS simulator
  4. Press Cmd-U to test and see xcode reports error:
  
 ### Actual Results:

```
Undefined symbols for architecture x86_64:
  "type metadata accessor for GoodApp.FirstViewController", referenced from:
      GoodAppTestsWithoutHost.GoodAppTestsWithoutHost.setUp() -> () in GoodAppTestsWithoutHost.o
      type metadata accessor for GoodApp.FirstViewController.Type in GoodAppTestsWithoutHost.o
ld: symbol(s) not found for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```

 ### Expected Results:
 
 `GoodAppTestsWithoutHost` should run tests just as `GoodAppTests` scheme.
