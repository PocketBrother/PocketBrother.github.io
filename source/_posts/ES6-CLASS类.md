---
title: ES6 CLASS类
date: 2021-03-24 18:23:00
tags:
---
> ## CLASS 类
> > 类表达式
> > ```javascript
> > const Person = class P{
> >     constructor (){
> >         P.a = 1;
> >         }
> > }
> > ```
> > 类的自执行
> > ```javascript
> > const Person = class P{
> >     constructor (){
> >         P.a = 1;
> >         }
> > }()
> > ```
> > 基本语法
> >  ```javascript
> > > class Car {
> > > 		//关键字【必须】
> > > 		constructor(wheel, color, length, width, speed) {
> > > 			this.wheel = wheel;
> > > 			this.color = color;
> > > 			this.lebgth = length;
> > > 			this.width = width;
> > > 			this.speed = speed;
> > > 			Car.totalCar += 1;
> > > 			console.log('一共创建了' + Car.totalCar + '辆车')
> > > 		}
> > > 		//自定义方法【可选】
> > > 		speedUp() {
> > > 			this.speed += 1;
> > > 		}
> > > 		//静态方法[创建的实例无法调用,只可以通过类本身调用]
> > > 		static repair(car) {
> > > 			console.log(`开始修理`);
> > > 			console.log(car);
> > > 			if (!car.speed) {
> > > 				car.speed = 0
> > > 			}
> > > 			console.log(`修理结束`);
> > > 			console.log(car);
> > > 		}
> > > 
> > > 		//自检程序
> > > 		checker() {
> > > 			console.log('开始自检');
> > > 			if (this.errors === 0) {
> > > 				console.log('检测完毕,一切正常')
> > > 			}
> > > 		}
> > > 
> > > 		//工厂检察院
> > > 		static checker() {
> > > 			console.log('我是市场检察员')
> > > 		}
> > > 	}
> > > 	//设置静态属性[通过类名.方式设置]
> > > 	Car.totalCar = 0;
> > > 	let maycar = new Car(3, '红色', 20, 40);
> > > 	let maycar2 = new Car(3, '红色', 20, 40);
> > > 	let maycar3 = new Car(3, '红色', 20, 40);
> > > 	maycar.checker();//调用共用方法
> > > 	Car.checker();//调用静态方法
> > > 	Car.repair(maycar)
> > > 
> > > ```
> >  ```

> > 类的基本用法--静态属性和方法
> >
> > ```javascript
> > //音乐播放器
> > class AudioPlayer {
> >     constructor (container){
> >         this.container = document.querySelector(container);
> >         this.songList=[];
> >         this.dom = null;
> >         this.status = 0
> >         this.audio = new Audio();
> >         this.getSongs();
> >         this.createElement();
> >         this.bindEvents();
> >         this.render()
> >     }
> >     //歌曲信息
> >     getSongs(){
> >         this.songList = [
> >             {
> >                 cover:'',//封面
> >        			url:'.mp3',//地址
> >                 singer:{},//歌手信息
> >                 name:''//歌名
> >             }
> >         ]
> >     }
> >     //生产dom
> >     createElement(){
> >         const div = document.createElement('div');
> >         div.innerHTML = `<div class="btn">播放按钮</div><div>进度条</div>`;
> >         this.dom = div;
> >     }
> >     
> >     //绑定事件
> >     bindEvents(){
> >         this.dom.querySelector('.btn').addEventListener('click',res=>{
> >             console.log('开始播放')
> >         })
> >     }
> >     
> >     render(){
> >         this.container.appendChild(this.dom)
> >     }
> > }
> >  new player('#app')
> > ```

> > getter和setter
> >
> > ```javascript
> > const obj = {
> >     _name:'',
> >     get name(){
> >         return this._name;
> >     },
> >     set name(val){
> >         this._name = val
> >     }
> > }
> > obj.name;
> > ```
> >
> > ES5 中为对象属性设置get和set方法  [Object.defineProperty]
> >
> > ```javascript
> > //一般用法
> > Object.defineProperty(obj,'name',{
> >      value:19,
> >     enumerable:true//表示这个默认属性是可以被遍历的
> > }
> > 
> > 给对象添加get和set方法                      
> > let obj = {
> >     _name:''
> > }
> > Object.defineProperty(obj,'name',{
> >     get :function(){
> >         return this._name
> >     }
> >     set :function(val){
> >     	this._name = val
> > 	}
> >    
> > })
> > ```
> >
> > 类的继承[<https://class.imooc.com/lesson/818#mid=22073>]
> >
> > ```javascript
> > class Human{
> >     constructor(name,age,sex,bobby){
> >         this.name = name;
> >         this.age = age;
> >         this.sex = sex;
> >         this.hobby = hobby
> >     }
> >     sesc(){
> >         const {name,age,sex,age} = this;
> >         console.log(`我叫${name},性别${sex},爱好${hobby},今年${age}`)
> >     }
> >     eat(){
> >         console.log('吧唧吧唧')
> >     }
> > }
> > 
> > class FEEngineer extends Human {
> >     
> >     constructor(name,age,sex,bobby,skill,salary){
> >         super(name,age,sex,bobby);
> >         this.skill = skill;
> >         this.salary = salary
> >     }
> > } 
> > new FEEngineer('刘浩','男',27,'打游戏',['js','h5','css'],'9k')
> > 
> > ```
