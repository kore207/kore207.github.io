---
title:  "memcmp를 통한 구조체 데이터의 변경 확인"
excerpt: "구조체의 비교"

categories:
  - Embedded  
  - C/CPP
last_modified_at: 2019-04-12T08:06:00-07:00
---

> (App개발시) 설정화면에서 값이 변경됐는지 Check 할때...

### 구조체의 비교

* 문자열 비교는 strcmp()로 처리하지만, 그외의 대부분은 memcmp()를 사용한다.
* 이 때 memcmp() 의 대상에 null 값이 있으면 안된다. 그 이유는 null 문자 뒤에는 쓰레기가 있는데 이들 쓰레기 까지 같은지 검사하기 때문에 정확하게 동작하지 않는다.
  *  이런경우 구조체 혹은 배열을 memset()과 같은방식으로 초기화 해서 사용한다.
  * 혹은 비교 함수를 만들어서 직접 사용한다.

```c
SettingValue setBack ; //SettingValue 구조체
memcpy(&setBack, &SetValue,sizeof(SettingValue)); //기존 사용하던 구조체로 copy (memset과 같은 원리 )
setBack = SettingRead(&setBack);

if(!memcmp(&setBack, &SetValue, sizeof(SettingValue)))
{ 
    ~~~
}
else
{
    ~~~
}
```

