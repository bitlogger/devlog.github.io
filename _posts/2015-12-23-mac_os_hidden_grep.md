---
layout: post
title:  "MAC OS hidden file grep"
author: "Pilsner"
date:   2015-12-23 21:00:00 +0900
categories: greping
---

# MAC OS hidden file grep 

얼마전에 한 프로젝트의 port번호를 알아내기 위해 설정파일을 뒤적거린 적이 있었습니다. 쉽게 찾질 못해서 `grep` 을 이용해 보려했지만 실패.. 결국 열심히 뒤져서 `.env`파일에 지정되어 있는 것을 찾아내긴 했습니다.    
근데 왜 grep에 안잡혔을까.. 의문이었습니다. 원인은 mac os.. linux에서는 grep이 숨겨진 파일까지 찾아주지만 mac os에서는 숨긴파일 및 폴더를 포함하지 않고 검색합니다.     
원인을 알고 찾기 위해 구글링을 했더니 꽤 여러가지 방법이 나왔습니다. 대부분이 find 와 grep 을 조합하는 방식이었는데 복잡합니다. 아주 간단하게 grep만으로 숨긴 파일 및 폴더에서 검색할 수 있는 방법이 있어 공유합니다. 

```
grep -r "example string" . # linux에서는 이렇게만 해도 숨긴 파일 및 폴더가 검색됩니다.
grep -r "example string" * .* # mac에서는 숨긴 파일 패턴을 더 추가해줘야합니다. 
```
주의해야 할 점은 mac에서 사용하고 있는 `.*` 패턴을 linux os에서 사용하면 부모폴더까지 검색해버립니다. `.*` 패턴에 `..` 패턴이 포함되기 때문입니다.   
알고 보면 엄청 간단하지만 혹시 저처럼 삽질하시는 분이 있을까봐 공유합니다. 
