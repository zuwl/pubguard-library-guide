# Adding the iOS Library manually

Please request the Pubguard Library from support@pubguard.com which will have the key embedded in it.

Once received copy the Pubguard.framework into your Xcode project and add it to all targets that will link to Pubguard:

![alt text](imgs/add.png)

Add the Pubguard Library to Target > General > Embedded Binaries. If you add the framework to "embedded binaries", the framework will also be added to "Linked Frameworks and Libraries".

![alt text](imgs/link.png)

![alt text](imgs/build-phase.png)

Select the build script from Build Phases

![alt text](imgs/select-build-script.png)

Add the following Build script

```
bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/Pubguard.framework/strip-frameworks.sh"
```

![alt text](imgs/add-build-script.png)

