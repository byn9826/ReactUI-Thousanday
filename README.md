# ReactUI-Thousanday
Some ReactUI components
---
##1. Install
```
npm install thousanday-react --save
```
Components List:<p>
[Rating Stars](#rate)<p>
[Upvote it](#upvote)<p>
[Inputbox character count](#inputbox)<p>

##<a name="rate">2. Rating Stars</a>
![Rating](https://raw.githubusercontent.com/byn9826/ReactUI-Thousanday/master/~pic/1.PNG)<p>
<table>
  <tr>
    <td>Params</td><td>example</td><td>Usage</td><td>Default</td>
  </tr>
  <tr>
    <td>rate</td><td>4</td><td>define the default stars</td><td>Must Define it</td>
  </tr>
  <tr>
    <td>length</td><td>5</td><td>define the maximum stars</td><td>Must Define it</td>
  </tr>
  <tr>
    <td>font</td><td>14px</td><td>adjust the size</td><td>18px</td>
  </tr>
  <tr>
    <td>color</td><td>black</td><td>define the color</td><td>orange</td>
  </tr>
  <tr>
    <td>change</td><td>yes</td><td>make it interactive</td><td>no</td>
  </tr>
  <tr>
    <td>rateChange</td><td>{this.rateChange.bind(this)}</td><td>Receive a rate from users</td><td></td>
  </tr>
</table>
[Simple Example](http://baozier.ca/react-rate)
###<b>2.1 use it as display only</b>
```
import {Rate} from 'thousanday-react';
<Rate rate="4" length="5"/>
<Rate rate="3" length="5" font="14px" color="black" />
```
Notice: You must define rate and length for every Rate component
###<b>2.2 use it to receive a rating from users</b>
```
import {Rate} from 'thousanday-react';
...
constructor(){
  super();
  this.state={
    defaultRate:"0"
  };
}
...
rateChange(rateNum){
  let prevState=this.state.defaultRate;
  this.setState({defaultRate:rateNum});
  //write code to update your database here
  //rateNum is the rating value from the users
}
...
<Rate rate={this.state.defaultRate} length="5" change="yes" rateChange={this.rateChange.bind(this)}/>
```
Notice:<p>
 ・You must use change="yes" to make this component interactive<p>
 ・You must define this.state.defaultRate as the default rate<p>
 ・rateChange(rateNum) will automaticlly get the rating value(which will be a number) from the users for you<p>

##<a name="upvote">3. Upvote it</a>
![Upvote](https://raw.githubusercontent.com/byn9826/ReactUI-Thousanday/master/~pic/2.PNG)<p>
<table>
  <tr>
    <td>Params</td><td>example</td><td>Usage</td><td>Default</td>
  </tr>
  <tr>
    <td>total</td><td>"0"</td><td>the total upvote number</td><td>Must Define it</td>
  </tr>
  <tr>
    <td>differ</td><td>"true"</td><td>Whether current user could upvote it or not</td><td>Must Define it</td>
  </tr>
  <tr>
    <td>color</td><td>"black"</td><td>content color</td><td>#1d4077(dark blue)</td>
  </tr>
  <tr>
    <td>bg</td><td>"black"</td><td>background color</td><td>"white"</td>
  </tr>
  <tr>
    <td>font</td><td>"13px"</td><td>size of the content</td><td>"11px"</td>
  </tr>
  <tr>
    <td>width</td><td>"5%"</td><td>width of the component</td><td>"3%"</td>
  </tr>
  <tr>
    <td>border</td><td>"1px solid black"</td><td>border of the component</td><td>"0"</td>
  </tr>
</table>
[Simple Example](http://baozier.ca/react-upvote)
###<b>3.1 use upvote</b><p>
The most simple way
```
import {Upvote} from 'thousanday-react';
<Upvote total="100" differ="false" />
```
However, we always need to change the total vote after click
```
import {Upvote} from 'thousanday-react';
...
constructor(props){
  super(props);
  this.state={
    defaultVote:"100",
    differ:"true" //make judgement about if users can vote or not (e.g.:can't vote for his own comment)
  };
}
upVote(){
  let prevState=this.state.defaultVote;
  this.setState({defaultVote:this.state.defaultVote+1});
  this.setState({differ:"false"});//after users click upvote, they can't click it again
  //interact with your database here to add total votes
}
...
render(){
  <Upvote total={this.state.defaultVote}  upVote={this.upVote.bind(this)} differ={this.state.differ}/>
}
```
##<a name="inputbox">4. Inputbox character count</a>
![Inputbox](https://raw.githubusercontent.com/byn9826/ReactUI-Thousanday/master/~pic/3.JPG)<p>
<table>
  <tr>
    <td>Params</td><td>example</td><td>Usage</td><td>Default</td>
  </tr>
  <tr>
    <td>content</td><td>"This is the old content"</td><td>Initial content in the input</td><td>""</td>
  </tr>
  <tr>
    <td>total</td><td>"50"</td><td>Maximum characters you allows in the input</td><td>Must Define it</td>
  </tr>
  <tr>
    <td>width</td><td>"150px"</td><td>width of the component</td><td>"100%"</td>
  </tr>
  <tr>
    <td>border</td><td>"1px dashed black"</td><td>border style of the input</td><td>"1px solid orange"</td>
  </tr>
  <tr>
    <td>height</td><td>"30px"</td><td>height of the input</td><td>"20px"</td>
  </tr>
  <tr>
    <td>fontSize</td><td>"15px"</td><td>fontsize inside the input</td><td>"13px"</td>
  </tr>
  <tr>
    <td>border</td><td>"1px solid black"</td><td>border of the component</td><td>"0"</td>
  </tr>
  <tr>
    <td>restrict</td><td>"off"</td><td>if user could still type after reach the maximum characters</td><td>"on"</td>
  </tr>
</table>
[Simple Example](http://baozier.ca/react-inputbox)
###<b>4.1 use inputbox character count</b><p>
```
import {Inputbox} from 'thousanday-react';
...
<Inputbox content="a simple one" total="50" />
<Inputbox content="allow input after reach maximum" total="50" restrict="off" width="150px" />
<Inputbox border="1px dashed orange" content="change style" total="50" width="200px"/>
```
You could get the updated input like this:
```
import {Inputbox} from 'thousanday-react';
...
constructor(props){
		super(props);
		this.state={
        content:"content from db",
		};
	}
...
submitInput(){
    let changedInput = this.refs.editInput.state.content;
    this.setState({content:changedInput});
    //update your db with variable changedInput
	}
...
<Inputbox ref="editInput" content={this.state.content} total="50" />

```

##License
MIT
