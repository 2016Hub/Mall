## 一、注册登录 user

- 注册： `/user/register`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              var email = $("#inputEmail").val();
              var pass = $("#inputPassword").val();
  
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/user/register",
                  data:{
                      "name":email,
                      "password":password,
                      "email":email,
                      "age":age
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script>
  ```

- 登录：`/user/login`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/user/login",
                  data:{
                      "email":email,
                      "password":pass
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script>
  ```

- 用户信息修改： `/user/change`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/user/change",
                  data:{
                      "user_id":user_id,
                      "name":name,
                      "email":email,
                      "age":age
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script>
  ```

- 用户密码修改： `/user/password`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/user/password",
                  data:{
                      "user_id":user_id,
                      "password":password
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script>
  ```

## 二、商品 item

- 商品列表页： `/item/list` 

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/item/list",
                  data:{
                      "classify":classify
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script>
  ```

- 商品详情：`/item/get`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/item/get",
                  data:{
                      "item_id":item_id
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script> 
  ```

## 三、订单 order

- 添加购物车或购买： `/order/order`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/order/order",
                  data:{
                      "item_id":item_id,
                      "user_id":user_id,
                      "price":price,
                      "amount":amount,
                      "classify":classify
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script> 
  ```

- 购物车详情或待支付、已支付等商品列表： `/order/shopping`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/order/shopping",
                  data:{
                      "classify":classify,
                      "user_id":user_id
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script> 
  ```

- 结算：`/order/count`

  ```js
  <script>
      $(function () {
          $("#button").click(function () {
              $.ajax({
                  type:"POST",
                  contentType:"application/x-www-form-urlencoded",
                  url:"http://localhost:8090/order/count",
                  data:{
                      "user_id":user_id,
                      item_ids:[id1,id2,...]
                  },
                  success:function (data) {
                      console.log(data)
                  },
                  error:function (data) {
                      console.log("error...")
                      console.log(data)
                  }
              })
          })
      })
  </script> 
  ```