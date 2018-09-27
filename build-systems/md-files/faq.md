## Tips

- `mvn clean install` usually run only in CI
    - `mvn install` avoid cleaning up all the artifacts
- `mvn install -pl $moduleName -am`
    - `-pl` build only specified modules
    - `-am` build only modules the target depends on
- `-offline` go offline, no new snapshot, less network traffic
- prefer module specific builds
- clean `.m2`
- keep modules smalls to avoid
    - huge compilation time
    - coupling
    - circular dependencies
- latest version of maven


## FAQ Session

Any doubts?
