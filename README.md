<h1 align="center">React Native Material Dialogs (Android)</h1>
<h4 align="center">Material Design Dialogs for React Native</h4>

[![npm version](https://badge.fury.io/js/react-native-material-dialogs.svg)](https://badge.fury.io/js/react-native-material-dialogs)
[![GitHub stars](https://img.shields.io/github/stars/arjunkomath/react-native-material-dialogs.svg)](https://github.com/arjunkomath/react-native-material-dialogs/stargazers)
[![Code Climate](https://codeclimate.com/github/arjunkomath/react-native-material-dialogs/badges/gpa.svg)](https://codeclimate.com/github/arjunkomath/react-native-material-dialogs)
[![Join the chat at https://gitter.im/arjunkomath/react-native-material-dialogs](https://badges.gitter.im/arjunkomath/react-native-material-dialogs.svg)](https://gitter.im/arjunkomath/react-native-material-dialogs?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![NPM](https://nodei.co/npm/react-native-material-dialogs.png?compact=true)](https://nodei.co/npm/react-native-material-dialogs/)

![](https://raw.githubusercontent.com/arjunkomath/react-native-material-dialogs/master/screenshots/Screenshot_2016-05-31-20-29-17.png)
![](https://raw.githubusercontent.com/arjunkomath/react-native-material-dialogs/master/screenshots/Screenshot_2016-05-31-20-29-41.png)
![](https://raw.githubusercontent.com/arjunkomath/react-native-material-dialogs/master/screenshots/Screenshot_2016-05-31-20-29-26.png)

## Install

Install the npm module.
```
npm i react-native-material-dialogs
```

### Plugin Installation (Android - Manual)

- In your android/settings.gradle file, make the following additions:
```
include ':react-native-material-dialogs'
project(':react-native-material-dialogs').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-material-dialogs')
```

- In your android/build.gradle file, add the a maven repository:
```
...
repositories {
    ...
    maven { url "https://jitpack.io" }
}
```
- In your android/app/build.gradle file, add the a compile-time dependency:
```
...
dependencies {
    ...
    compile project(':react-native-material-dialogs')
}
```
- Next, you need to change the MainActivity of your app.

```java
import com.arjunkomath.react.MaterialDialogPackage; // <--- Add This

...
/**
     * A list of packages used by the app. If the app uses additional views
     * or modules besides the default ones, add more packages here.
     */
    @Override
    protected List<ReactPackage> getPackages() {
        return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
                new MaterialDialogPackage(this) // "this" is very important!
        );
    }
```

And, you're done!

## Usage

```
import MaterialDialog from 'react-native-material-dialogs';
```

There are two types of dialogs:

### Dialog with one feedback

```
MaterialDialog.show('Yaaay!!', 'Success', 'done', MaterialDialog.SUCCESS,
      () => {
        console.log('asd');
      });
```

Parameters:

```
MaterialDialog.show( <Title> , <Description>, <Button text>, <Type>, <Callback>);
```

### Dialog with two feedbacks

```
MaterialDialog.showWithCancel('Danger!', 'Are you sure?', 'YES', 'NO', MaterialDialog.DANGER,
      () => {
        console.log('yes');
      },
      () => {
        console.log('no');
      });
```

Parameters:

```
MaterialDialog.show( <Title> , <Description>, <Positive Button text>, <Negative Button text>, <Type>, <Callback Positive>, <Callback Negative>);
```

Title, Description and Button text are of type String. While Type is a constant.
There are four types:

```
MaterialDialog.SUCCESS
MaterialDialog.INFO
MaterialDialog.WARNING
MaterialDialog.DANGER
```

## Example

```jsx
import React, { Component } from 'react';
 import {
  AppRegistry,
  StyleSheet,
  Text,
  View,
  TouchableOpacity
} from 'react-native';

import MaterialDialog from 'react-native-material-dialogs';

class dialog_test extends Component {

  press() {
    MaterialDialog.show('Yaaay!!', 'Success', 'done', MaterialDialog.SUCCESS,
      () => {
        console.log('done');
      });
  }

  render() {
    return (
      <View style={styles.container}>
      <TouchableOpacity onPress={this.press}>
      <Text style={styles.welcome}>
      Press me to see dialog!
      </Text>
      </TouchableOpacity>
      </View>
      );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  }
});

AppRegistry.registerComponent('dialog_test', () => dialog_test);
```

## :two_hearts: Thanks
[MaterialStyledDialogs](https://github.com/javiersantos/MaterialStyledDialogs)

## About Author
Built with <3 by Arjun Komath / [arjunkomath@gmail.com](mailto:arjunkomath@gmail.com)
