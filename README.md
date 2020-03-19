# react-native-yearpicker [![Build Status](https://travis-ci.org/xgfe/react-native-datepicker.svg?branch=master)](https://travis-ci.org/xgfe/react-native-datepicker) [![Coverage Status](https://coveralls.io/repos/github/xgfe/react-native-datepicker/badge.svg?branch=master)](https://coveralls.io/github/xgfe/react-native-datepicker?branch=master) 
React Native YearPicker component for iOS, using DatePickerIOS to display a modal picker to select year value.  Fork from react-native-datepicker, which includs functionality for  Android using DatePickerAndroid and TimePickerAndroid

## Install

```bash
npm install react-native-yearpicker --save
```

Or using [react-native-ui-xg](https://github.com/xgfe/react-native-ui-xg), our react-naitve ui kit.

```bash
npm install react-native-ui-xg --save
```

## Example


## Usage

```javascript

import React, { Component } from 'react'
import YearPicker from 'react-native-yearpicker'

export default class MyYearPicker extends Component {
  constructor(props){
    super(props)
    this.state = {date:"2016-05-15"}
  }

  render(){
    return (
      <YearPicker
        style={{flex:.9, paddingBottom:10}}
        date={this.state.class_year_alum}
        mode= "date" // for date with time: "datetime"

        placeholder="Year"
        format="YYYY" 
        // minYear= "1992" // Not reqiured. 
        maxYear="2020"  
        confirmBtnText="Done"
        cancelBtnText="" 
        onDateChange={(date) => {this._setdate(date)} }
        yearIndex = {this.state.yearIndex } // to display currently selected year -> {this.props.yearIndex}. 
        year = {this.state.year} // this.props.year for currently selected year
        isEnabled =  {this.state.isEnabled}
        customStyles={{ 
            datePicker: { 

            },
            dateText: {
            fontSize: 20,
            },
            btnTextConfirm: {
                color: '#007AFE',
                fontWeight: 'bold',
            },
            btnTextCancel: {
                color: '#007AFE',
            },
            placeholderText: {
                fontSize:20,
            },
            dateInput: {
                alignItems: 'flex-start',
                backgroundColor: '#fff',
                marginHorizontal: 10,
                marginVertical: 5,
                paddingVertical: 5,
                paddingHorizontal: 5,
                height: 50,
            }
            // ... You can check the source to find the other keys.
        }}


        />
  
       
    )
  }
}
```

You can check [index.js](https://github.com/xgfe/react-native-datepicker/blob/master/index.android.js) in the Example for detail.

## Properties

| Prop  | Default  | Type | Description |
| :------------ |:---------------:| :---------------:| :-----|
| style | - | `object` | Specify the style of the DatePicker, eg. width, height...  |
| date | - | <code>string &#124; date &#124; Moment instance</code> | Specify the display date of DatePicker. `string` type value must match the specified format |
| mode | 'date' | `enum` | The `enum` of `date`, `datetime` and `time` |
| androidMode | 'default' | `enum` | The `enum` of `default`, `calendar` and `spinner` (only Android) |
| format | 'YYYY-MM-DD' | `string` | Specify the display format of the date, which using [moment.js](http://momentjs.com/). The default value change according to the mode. |
| confirmBtnText | '确定' | `string` | Specify the text of confirm btn in ios. |
| cancelBtnText | '取消' | `string` | Specify the text of cancel btn in ios. |
| iconSource | - | <code>{uri: string} &#124; number</code> | Specify the icon. Same as the `source` of Image, always using `require()` |
| minDate | - | <code>string &#124; date</code> | Restricts the range of possible date values. |
| maxDate | - | <code>string &#124; date</code> | Restricts the range of possible date values. |
| duration | 300 | `number` | Specify the animation duration of datepicker.|
| customStyles | - | `object` | The hook of customize datepicker style, same as the native style. `dateTouchBody`, `dateInput`...|
| showIcon | true | `boolean` | Controller whether or not show the icon |
| hideText | false | `boolean` | Controller whether or not show the `dateText` |
| iconComponent | - | `element` | Set the custom icon |
| disabled | false | `boolean` | Controller whether or not disable the picker |
| is24Hour | - | `boolean` | Set the TimePicker is24Hour flag. The default value depend on `format`. Only work in Android |
| allowFontScaling | true | `boolean` | Set to false to disable font scaling for every text component |
| placeholder | '' | `string` | The placeholder show when this.props.date is falsy |
| onDateChange | - | `function` | This is called when the user confirm the picked date or time in the UI. The first and only argument is a date or time string representing the new date and time formatted by [moment.js](http://momentjs.com/) with the given format property. |
| onOpenModal | - | `function` | This is called when the DatePicker Modal open. |
| onCloseModal | - | `function` | This is called when the DatePicker Modal close |
| onPressMask | - | `function` | This is called when clicking the ios modal mask |
| modalOnResponderTerminationRequest | - | `function` | Set the callback for React Native's [Gesture Responder System](https://facebook.github.io/react-native/docs/gesture-responder-system.html#responder-lifecycle)'s call to `onResponderTerminationRequest`. By default this will reject a termination request, but can be overidden in case the View under the Modal is implementing custom gesture responders, and you wish for those to be overidden in certain cases.  |
| TouchableComponent | `TouchableHighlight` | `Component` | Replace the `TouchableHighlight` with a custom `Component`. For example : `TouchableOpacity` |
| getDateStr | - | Function | A function to override how to format the date into a `String` for display, receives a `Date` instance

### Property `customStyles` available keys

* appearance: `dateInput`, `disabled`, `dateTouchBody`, `dateIcon`, `placeholderText`, `dateText`
* ios select panel: `datePickerCon`, `datePicker`, `btnConfirm`, `btnTextConfirm`, `btnCancel`, `btnTextCancel`


## Instance Methods

| Method  | Params  | Description |
| :------------ |:---------------:| :---------------:|
| onPressDate | - | Manually open the date picker panel |
| onPressCancel | - | Manually close the date picker panel like, similarly pressing cancel btn |
