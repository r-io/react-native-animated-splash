# [react-native-animated-splash](https://www.npmjs.com/package/react-native-animated-splash)
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)
![Supports Android and iOS](https://img.shields.io/badge/platforms-android%20|%20ios-lightgrey.svg?style=flat-square)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
[![NPM](https://img.shields.io/npm/dm/react-native-animated-splash)](https://www.npmjs.com/package/react-native-animated-splash)
[![Version](https://img.shields.io/npm/v/react-native-animated-splash)](https://www.npmjs.com/package/react-native-animated-splash)


React-Native-Animated-Splash is developed to help the react-native developers in speeding-up their development process. This package leverages the developer in implementing native animations by using our builtin classes for animation with easy to use api, all the animations run on native thread for smooth performance.
##### Objective
The main objective or the edge of this module is that, splash animation runs in parallel with loading of javascript, which means when animation is running, javascript is being loaded in parallel behind the scenes, moreover componentDidMount can also be called for any api hits before calling hide function of splash from react-native side.

### Only available for Android, iOS will be available soon

### Installation
If you prefer **npm**,
```sh
$ npm install react-native-animated-splash --save
```

If you prefer **yarn**,
```sh
$ yarn add react-native-animated-splash
```


## USAGE

 ###  Android
 >
 Following are the basic examples of using react-native-animated-splash. Go to your MainActivity.java file and add following code.
 
#### Example Animation 1
 
 ```sh
    
package com.example;

import android.os.Bundle;


import com.facebook.react.ReactActivity;
import com.blitzapp.animatedsplash.animation.GroupAnimation;
import com.blitzapp.animatedsplash.animation.AddImageView;
import static com.blitzapp.animatedsplash.animation.Splash.DIALOGSLIDEDOWN;
import static com.blitzapp.animatedsplash.animation.Splash.FADE;
import static com.blitzapp.animatedsplash.animation.Splash.performSingleAnimation;
import static com.blitzapp.animatedsplash.animation.Splash.createSplashView;
import static com.blitzapp.animatedsplash.animation.Splash.screenHeight;
import static com.blitzapp.animatedsplash.animation.Splash.screenWidth;
import static com.blitzapp.animatedsplash.animation.Splash.setBackgroundColor;
import static com.blitzapp.animatedsplash.animation.Splash.setSplashHideAnimation;
import static com.blitzapp.animatedsplash.animation.Splash.setSplashHideDelay;
import static com.blitzapp.animatedsplash.animation.Splash.splashShow;


public class MainActivity extends ReactActivity {

    @Override
    protected String getMainComponentName() {
        return "example";
    }

    public void onCreate(Bundle saved) {
        super.onCreate(saved);
        initiateSplash();
    }

    public void initiateSplash() {
    
        // create dialog
        splash.createSplashView(MainActivity.this);

        //set background color to view
        setBackgroundColor("#101010");
        
        // set splash hide animation
        setSplashHideAnimation(DIALOGSLIDEDOWN);
        
        // set splash hide delay
        setSplashHideDelay(1500);
        
        // create and add images to view
        AddImageView logoimage = new AddImageView(R.drawable.logo, screenHeight * 0.24, screenWidth * 0.4, getCenterX(screenWidth * 0.41), getCenterY(screenHeight * 0.26), 0, FIT_CENTER, false);

        AddImageView image1 = new AddImageView(R.drawable.oval3, screenHeight * 0.39, screenWidth * 0.76, getCenterX(screenWidth * 0.76), getCenterY(screenHeight * 0.39), 0, FIT_XY, false);

        AddImageView image2 = new AddImageView(R.drawable.oval2, screenHeight * 0.537, screenWidth + screenWidth * 0.06, getCenterX(screenWidth + screenWidth * 0.06), getCenterY(screenHeight * 0.537), 0, FIT_XY, false);

        AddImageView image3 = new AddImageView(R.drawable.oval1, screenHeight * 0.676, screenWidth + screenWidth * 0.29, getCenterX(screenWidth + screenWidth * 0.29), getCenterY(screenHeight * 0.676), 0, FIT_XY, false);


        // add group animation
        GroupAnimation group1 = new GroupAnimation();
        group1.performGroupAnimation(logoimage, FADE, 400, 0f, 1f, false);
        group1.performGroupAnimation(logoimage, SCALE, 400, 0f, 1f, 0f, 1f, false);
        
        // add single animation
        performSingleAnimation(image1, FADE, 500, 0f, 1f);

        performSingleAnimation(image2, FADE, 400, 0f, 1f);

        performSingleAnimation(image3, FADE, 400, 0f, 1f);

        splashShow();

    }
}


```
Then call hide function of splash in your app, from react native side like this:
 
 ```sh
 import AnimatedSplash from "react-native-animated-splash";
 
 AnimatedSplash.hide()
 ```  
 
![](https://github.com/Blitz-Mobile-Apps/react-native-animated-splash/blob/master/example1.gif?raw=true)
![](https://github.com/Blitz-Mobile-Apps/react-native-animated-splash/blob/master/example1ios.gif?raw=true)
>
>
#### Example Animation 2

```sh
package com.example;

import android.os.Bundle;


import com.blitzapp.animatedsplash.animation.AddImageView;
import com.blitzapp.animatedsplash.animation.GroupAnimation;
import com.facebook.react.ReactActivity;

import static com.blitzapp.animatedsplash.animation.Splash.DIALOGSLIDELEFT;
import static com.blitzapp.animatedsplash.animation.Splash.SCALE;
import static com.blitzapp.animatedsplash.animation.Splash.SLIDE;
import static com.blitzapp.animatedsplash.animation.Splash.createSplashView;
import static com.blitzapp.animatedsplash.animation.Splash.performSingleAnimation;
import static com.blitzapp.animatedsplash.animation.Splash.screenHeight;
import static com.blitzapp.animatedsplash.animation.Splash.screenWidth;
import static com.blitzapp.animatedsplash.animation.Splash.setBackgroundImage;
import static com.blitzapp.animatedsplash.animation.Splash.setSplashHideAnimation;
import static com.blitzapp.animatedsplash.animation.Splash.setSplashHideDelay;
import static com.blitzapp.animatedsplash.animation.Splash.splashShow;


public class MainActivity extends ReactActivity {


    @Override
    protected String getMainComponentName() {
        return "example";
    }


    public void onCreate(Bundle saved) {
        super.onCreate(saved);
        initiateSplash();
    }

    public void initiateSplash() {
        
        //create dialog
        createSplashView(MainActivity.this);

        //set background
        setBackgroundImage(R.drawable.splashbg);
        
        // set splash hide animation
        setSplashHideAnimation(DIALOGSLIDELEFT);

        // set splash hide delay
        setSplashHideDelay(1500);

        // Create and add images to view
        AddImageView image1 = new AddImageView(R.drawable.header, screenHeight * 0.15, screenWidth, 0, 0, FIT_XY, false);
        AddImageView image2 = new AddImageView(R.drawable.footer, screenHeight * 0.15, screenWidth, 0, screenHeight - screenHeight * 0.15, FIT_XY, false);
        AddImageView logoimage = new AddImageView(R.drawable.logo2, screenHeight * 0.18, screenWidth * 0.45, getCenterX(screenWidth * 0.45), getCenterY(screenHeight * 0.18), FIT_XY, false);

        // add group animation
         GroupAnimation group1 = new GroupAnimation();
        group1.performGroupAnimation(image1, SLIDE, 780, 0f, 0f, -screenHeight * 0.15f, 0f);
        group1.performGroupAnimation(image2, SLIDE, 780, 0f, 0f, screenHeight * 0.15f, 0f);
        
        
        // add single animation
        performSingleAnimation(logoimage, SCALE, 780, 0.2f, 1f, 0.2f, 1f);

        splashShow();

    }
}
```
Then call hide function of splash in your app, from react native side like this:
 
 ```sh
 import AnimatedSplash from "react-native-animated-splash";
 
 AnimatedSplash.hide()
 ```  
 
 ![](https://github.com/Blitz-Mobile-Apps/react-native-animated-splash/blob/master/example2.gif?raw=true)
  ![](https://github.com/Blitz-Mobile-Apps/react-native-animated-splash/blob/master/example2ios.gif?raw=true)
 >
 >
#### Important Note

> add respective images from your drawable else it will give error
>
> for some variables which appears not defined like "screenHeight", import them from library class.
>

>
>
#### [Android Usage with Method Descriptions](./androidDesction.md)
### Todos
We aim to make this package even more robust and powerful by adding following features in the upcoming releases:
 - implement ios
 [Contribution guidelines for this project](./IosUsage.md)

License
MIT 
