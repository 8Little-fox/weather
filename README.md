# weather
小程序简易版天气预报

定义城市，天气，温度，风级，图片，日期参数，穿衣提示，星期
```
var defaultcity, getweather, gettemp, getwind, getpic, getdate, gettips, getweek
```

请求天行数据天气api

```
  wx.request({
      url: 'http://api.tianapi.com/txapi/tianqi/index',
      data: {
        key: '2c2fbc8613a3d706706d43a7f17b7b1f',
        method: "GET",
        city: defaultcity
      },
      success: res => {
        console.log(res.data)
        if (!res.data) {
          console.log('获取天气接口失败')
          return
        }
        getweather = res.data.newslist[0].weather
        gettemp = res.data.newslist[0].real
        getwind = res.data.newslist[0].wind
        getpic = res.data.newslist[0].weatherimg
        getdate = res.data.newslist[0].date
        gettips = res.data.newslist[0].tips
        getweek = res.data.newslist[0].week
        this.setData({
          city: defaultcity,
          weather: getweather,
          temp: gettemp,
          wind: getwind,
          pic: getpic,
          date: getdate,
          tips: gettips,
          week: getweek
        })
        console.log(res)
        wx.hideLoading()
      }

    })
```

  请求天气语句api
```
   wx.request({
      url: 'http://api.tianapi.com/txapi/tianqishiju/index?key=2c2fbc8613a3d706706d43a7f17b7b1f',
      success: res => {
        if (res.data.code == 200) {
          this.setData({
            content: res.data.newslist[0].content
          })
        } else {
          this.setData({
            content: res.data.msg
          })
        }
      }
    })
```
