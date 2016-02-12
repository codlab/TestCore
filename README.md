# TestCore

This library provides few Utility classes and instantiations to help common tests to be done via Robolectric and JUnit for Android.

# Integration

```gradle
buildscript {
    repositories {
        ...
        maven { url "https://jitpack.io" }
    }
}
```

```gradle
dependencies {
    testCompile 'junit:junit:4.12'
    testCompile 'org.robolectric:robolectric:3.0'
    testCompile 'org.robolectric:shadows-support-v4:3.0'
    
    testCompile 'com.github.codlab:TestCore:0.2.3'
}
```

# Usage

Few methods are here to help you test out few common structures in java code 

## Public class standard constructor

```java
  TestUtil.assertPublicClassWellDefined(final Class<?> clazz)
```

Will assert that the class has a valid public Constructor()

## Assert an Utility class definition

```java
  TestUtil.assertUtilityClassWellDefined(final Class<?> clazz)
```

Will assert that the utility class is well defined. i.e :
- final class
- default constructor
- only one constructor
- private constructor
- only static methods

## Assert a Singleton class is well defined

```java
  TestUtil.assertSingletonClassWellDefined(final Class<?> clazz)
```

Will assert that the class is a singleton

## Purge the Robolectric activity started stack

```java
  TestUtil.purgeShadowActivityStartActivity(ShadowActivity shadowActivity)
```

Sometimes, you need to check for startActivity() results but you can have multiple previous call done earlier.
This method makes sure the stack is cleared out when it returns. Use it before any test method where you require a startActivity to be tested
