    |>    
  \___/  


為了方便更新Model時，前端可以同步收到通知更新，所以寫了 sailsx2.js 
來整合Socket.IO進行Model更新通知


使用方式如下


Step1. 後端建立Model
===================

你必須先在後端有建立Model才能使用，建立Model方式很簡單，一行指令就可以完成

> sails generate api Item

Step2. 前端使用Model
===================

先建立用來完成Model 建立、修改、查詢、刪除的物件 itemIO
var itemIO = new x2('http://localhost:1337/Item',
	{
		message:function(msg){
		   // 後端通知異動更新...
		}
	});

//建立Item物件
var item = new Item( {name: 'Batman' , age: 37} );

//保存到後端
itemIO.create(item , function(item){
	console.log('created',item);
});

//修改Item物件
item.set('age',38);
itemIO.update(item);

