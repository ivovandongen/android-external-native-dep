# Example external native dependency setup


Useful in cases you want to develop a library in conjunction with an app where they are not in the same project.

In this case the `main` project depends on the `library` project and are situated next to each other on the FS.

The main project declares a project dependency on the library in the [build.gradle](https://github.com/ivovandongen/android-external-native-dep/blob/master/main/app/build.gradle). 

```
dependencies {
    implementation project(':lib')
    ...
}
```

To be able to find the project, the location on the FS is specified in the [settings.gradle](https://github.com/ivovandongen/android-external-native-dep/blob/master/main/settings.gradle):

```
project(':lib').projectDir = file('../library/lib')
```

If the library is not a direct dependency of the project, it might need to be excluded from the direct dependency to make sure it is picked up correctly. See https://docs.gradle.org/current/userguide/managing_transitive_dependencies.html
