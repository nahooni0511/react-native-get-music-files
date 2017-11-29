
# react-native-get-music-files

## Getting started

`$ npm install react-native-get-music-files --save`

### Mostly automatic installation

`$ react-native link react-native-get-music-files`

### Manual installation


#### iOS (WIP NOT READY)

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-reat-native-get-music-files` and add `RNReatNativeGetMusicFiles.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNReatNativeGetMusicFiles.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import com.reactlibrary.RNReatNativeGetMusicFilesPackage;` to the imports at the top of the file
  - Add `new RNReatNativeGetMusicFilesPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-get-music-files'
  	project(':react-native-get-music-files').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-get-music-files/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-get-music-files')
  	```
  
# react-native-get-music-files
React Native package to get music files from local and sd for Android (only)

# What does this package?

This package get all the sound files in your local and sd card (Android only), and retrive metadata from each file, also generate an blurred image from cover file.

* SongID
* Title
* Author
* Album
* Duration
* Path
* Cover
* Duration
* Lyrics
* Date
* Genre
* Comments

## Usage
```
import MusicFiles from 'react-native-get-music-files';

MusicFiles.getAll({
    blured : true, // works only when 'cover' is set to true
    artist : true,
    duration : true, //default : true
    cover : false, //default : true,
    genre : true,
    title : true,
    cover : true,
    date : true,
    lyrics : true,
    comments : true
    minimumSongDuration : 10000 // get songs bigger than 10000 miliseconds duration
},(error) => {
    alert("ERROR: " + error);
},(response) => {
    alert(JSON.stringify(response));
});
```

MusicFiles returns an array of objects where you can loop, something like this.

```
[
  {
    id : 1,
    title : "La danza del fuego",
    author : "Mago de Oz",
    album : "Finisterra",
    genre : "Folk",
    duration : 132132312321, // miliseconds
    cover : "file:///sdcard/0/123.png",
    blur : "file:///sdcard/0/123-blur.png", //Will come null if createBLur is set to false
    path : "/sdcard/0/la-danza-del-fuego.mp3",
    date : "2017",
    lyrics : "[00:00] Cuando despiertes un dia..."
  }
]
```

# TODO

- [ ] iOS Version
- [x] Android Version
- [x] Optional parameters
- [x] Speed up retriving songs (run in another thread)

PR are welcome!