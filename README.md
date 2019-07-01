## 数据表

- `user`

  ```sql
  {
  	id //string
  	name
  	password
  	email
  	age //int
  }
  ```

- `item` 

  ```sql
  {
  	id //int
  	name
  	description
  	price //int
  	time
  	classify //int
  }
  ```

- `item_stock`

  ```sql
  {
  	id //int
  	stock //int
  }
  ```

- `order`

  ```sql
  {
  	id //string
  	user_id //string
  	item_id //int
  	price //int
  	amount //int
  	classify //int
  }
  ```

## 一、注册登录 user

- 注册： `/user/register`

  - 前端请求：

    ```json
    {
        name
        password
        email
        age //int
    }
    ```

  - 后台返回：

    ```json
    {
        "status": "success",
        "data": null
    }
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    ```

- 登录：`/user/login`

  - 前端请求：

    ```json
    {
        email
        password
    }
    ```

  - 后台返回： 存到缓存里面(如： localStorage)

    ```json
    {
        status: "success"
        data: {
        	token 
            user: {
    			id //string
                name
                email
                age
            }
    	}
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    ```

- 用户信息修改： `/user/change`

  - 前端请求：

    ```json
    {
        user_id //string
        name
        email
        age //int
    }
    
    ```

  - 后台返回： 

    ```json
    {
        status: "success"
        data: {
        	token 
            user: {
    			id //string
                name
                email
                age
            }
    	}
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    
    ```

- 用户密码修改： `/user/password`

  - 前端请求： 

    ```json
    {
        user_id //string
        password
    }
    
    ```

  - 后台返回：

    ```json
    {
        status: "success"
        data: null
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    
    ```

## 二、商品 item

- 商品列表页： `/item/list`

  - 前端请求： 

    ```json
    {
        classify //int --> 1 椅子，2 柜子 3 床 4 沙发
    }
    
    ```

  - 后台返回：

    ```json
    {
        status: "success"
        data: [
        	{
        		id //int
        		name
        		description
        		price
        		time
        		stock //int 库存
    		}
        ]
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    
    ```

- 商品详情：`/item/get`

  - 前端请求： 

    ```json
    {
        item_id //int
    }
    
    ```

  - 后台返回： 

    ```json
    {
        status: "success"
        data: {
        	id //int 
        	name
        	description
        	price
        	time
        	stock //int 库存
    	}
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    
    ```

## 三、订单 order

- 添加购物车或购买： `/order/order`

  - 前端请求： 

    ```json
    {
        item_id //int
        user_id //string
        price
        amount
        classify //int --> 0 添加购物车 1 购买
    }
    
    ```

  - 后台返回：

    ```json
    {
        status: "success"
        data: {
        	classify //int --> 0 添加购物车 1 购买(则跳转到支付界面)
    	}
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    
    ```

- 购物车详情或待支付、已支付： `/order/shopping`

  - 前端请求： 

    ```json
    {
        user_id //string
        classify //int --> 0 未结算(购物车详情或待支付) 1 已结算(已支付)
    }
    
    ```

  - 后台返回： 

    ```json
    {
        status: "success"
        data: [
        	{
        		id //int 
        		name
        		price
    			amount    		
    		},
    		{
                ...
            }
        ]
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    ```

- 结算：`/order/count`

  - 前端请求： 

    ```json
    {
        user_id //string
        item_id: [id1,id2,...]
    }
    ```
    
- 后台返回：
  
  ```json
    {
        status: "success"
        data: null
    } 
    或
    {
        "status": "fail",
        "data": {
            "errCode": 30002,
            "errMsg": "账号或密码错误，请重试"
        }
    }
    ```