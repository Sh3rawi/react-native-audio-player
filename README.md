# react-native-audio-player
A React Native module to play audio on Android

## Installation

First you need to install react-native-audio-player:

```javascript
npm install react-native-audio-player --save
```


### Installation (Android)

* In `android/setting.gradle`

```gradle
...
include ':RNAudioPlayer', ':app'
project(':RNAudioPlayer').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-audio-player/android')
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
    ...
    compile project(':RNAudioPlayer')
}
```

* register module (in MainActivity.java)

```java
import com.sh3rawi.RNAudioPlayer.*;  // <--- import

public class MainActivity extends Activity implements DefaultHardwareBackBtnHandler {
  ......

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    mReactRootView = new ReactRootView(this);

    mReactInstanceManager = ReactInstanceManager.builder()
      .setApplication(getApplication())
      .setBundleAssetName("index.android.bundle")
      .setJSMainModuleName("index.android")
      .addPackage(new MainReactPackage())
      .addPackage(new RNAudioPlayer())              // <------ add here
      .setUseDeveloperSupport(BuildConfig.DEBUG)
      .setInitialLifecycleState(LifecycleState.RESUMED)
      .build();

    mReactRootView.startReactApplication(mReactInstanceManager, "ExampleRN", null);

    setContentView(mReactRootView);
  }

  ......

}
```
## Audio Resources
  
  Please put you audio resources in android/app/src/main/res/raw
  
  
(Thanks to @chirag04 for writing the instructions) - And thanks for @rebeccahughes as I followed her react-native-device-info to make this work!

## Example

```js
var AudioPlayer = require('react-native-audio-player');

AudioPlayer.play('example_tone');
```
