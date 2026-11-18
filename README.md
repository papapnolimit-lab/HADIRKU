codemagic.yaml

workflows:
  hadirku-android:
    name: HadirKu Android APK
    max_build_duration: 60
    instance_type: mac_mini_m2

    scripts:
      - name: Set Android SDK location
        script: |
          echo "sdk.dir=$ANDROID_SDK_ROOT" > "$CM_BUILD_DIR/local.properties"

      - name: Build Android APK
        script: |
          java -classpath gradle/wrapper/gradle-wrapper.jar org.gradle.wrapper.GradleWrapperMain assembleDebug

    artifacts:
      - app/build/outputs/apk/debug/*.apk

