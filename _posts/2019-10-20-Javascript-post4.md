---
layout: post
title: "OpenWeatherMap API 이용하여 현재 위치와 날씨정보 가져오기"
excerpt: ""
categories: [Javascript]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


## OpenWeather API 이용하여 현재 위치와 날씨정보 가져와서 화면에뿌려보자

일단 https://openweathermap.org/current 사이트에 가입하고,
내 API Key 값을 가져온다.

로그인을 하면 이런 화면이 보이고 생성된 키값을 사용하면 된다.
<img src="https://miro.medium.com/max/2712/1*iZjgsfeaHEXoiVRfgFjpzA.png" />


## navigator.geolocation.getCurrentPosition 메서드를 이용하여 사용자의 현재 위치 확인

```javascript

  function askForCoords(){
    navigator.geolocation.getCurrentPosition(handleGeoSucces, handleGeoError);
  }

```
askForCoords() 함수를 만들어서
navigator.geolocation.getCurrentPosition 메서드를 이용해서 사용자 위치를 확인할 수 있다.

`navigator.geolocation.getCurrentPosition(success[, error[, [options]])`

- success: Position 객체를 유일한 매개변수로 받는 콜백 함수.
- error (Optional): PositionError 객체를 유일한 매개변수로 받는 콜백 함수.
- options (Optional): PositionOptions 객체.


```javascript

  function handleGeoSucces(position){
    const latitude =  position.coords.latitude;
    const longitude = position.coords.longitude;
    const coordsObj = {
      latitude,
      longitude
    };
    saveCoords(coordsObj);
    getWeather(latitude, longitude);
  }

  function handleGeoError(position){
    console.log('Cant get your position.');
  }

```



## 좌표값을 이용해서 날씨 가져오기

### openweathermap 페이지에서 아래 API 사용법 확인
<img src="https://miro.medium.com/max/3012/1*KbhROEwz6OCRyVHPIiwQ-Q.png" />

### 좌표를 이용해서 값을 가져오는 방법 확인
<img src="https://miro.medium.com/max/1976/1*Qky0NPHaWiNRK76Eqo_yHg.png" />



```javascript

  function getWeather(lat, lon){
    fetch(
      `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${API_KEY}&units=metric`
    )
      .then(function(response){
      return response.json();
    })
      .then(function(json){
        console.log(json);
        const temparature = json.main.temp;  //온도
        const place = json.name;   // 사용자 위치
        weather.innerText = `${temparature} @${place}`;

      });
  }

```


getWeather() 함수를 생성해 좌표를 넘겨서 정보를 받아왔다. 
받아온 API response 는 json객체 형태이며, 온도 뿐만 아니라 다양한 날씨정보를 확인할 수 있다.

나는 temp 와 사용자 위치 지역명인 name 항목을 가져왔다.

<img src="https://miro.medium.com/max/2332/1*_sAVAeD7NySLSPu6pFQB5g.png" />
