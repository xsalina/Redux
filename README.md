# Redux
步骤及笔记



redux 订阅模式


1、安装redux

            yard add redux



2、引入createStore,相当于一个商店
           
	import {createStore} from “redux”




3、创建这个商店接受这个纯函数比如reducer，这个函数的执行体就是你要来这个商店做的事。然后用变量store存起来

       	const store = createstore（reducer）


	//这个函数处理改变state状态的事件，此时的state可以是对象、数组、数字，默认状态为0
	function reducer（state=0，action）{
  		switch（action.type）{
      		case “addnum”：
            		return  state+5
      		case “reducenum”：
            		return state-5
     		default：
            		return 0

  		}

	}



4、要去改变state就要调用store里面的dispatch执行函数，并传入一个action的type类型以对象的形式，这个就是你要去做什么事，买什么东西一样。

	A、这是type类型为addnum并执行，使得state在原先基础上+5
	store.dispatch（{
     	       type：“addnum”
	}）


	B、这是type类型为reduce并执行了，使得state在原先基础上-5
	store.dispatch（{
     	       type：“reducenum”
	}）




5、改变了state之后就可以通过store.getState（）得到新的数据，这个就相当于你买的东西,接收到的新的state获取的方法

	store还提供了一个方法（subscribe）监听数据变化接受一个函数名

	store.subscribe（listener）

	function listener（）{
    	        //currenState是得到新的state
    	          const  currentState = store.getState（）
    	          console.log（currenState）
	}
