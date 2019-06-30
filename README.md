### README



## 一、注册登录

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

## 二、商品

- 商品详情：`/item/get`

  - 前端请求： 

    ```json
    {
        item_id //int
        user_id //string
        token
    }
    ```

  - 后台返回： 

    ```json
    {
        status: "success"
        data: {
        	name
        	description
        	price
        	time
        	stock
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

- 添加购物车： ``

  - 前端请求： 

    ```json
    {
        token
        item_id //int
        user_id //int
        price //int
        amount //int
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

- 购物车详情：

  - 前端请求：

    ```json
    {
        token
        user_id //int
    }
    ```

  - 后台返回：

    ```json
    {
        [
            {
    			name
                description
                price
                amount
            },
            {
    			...
            }
        ]
    }
    ```

- 结算：

  - 前端请求： 

    ```json
    {
        token
        user_id //int
    }
    ```

  - 后台返回：

    ```json
    {
        
    }
    ```
