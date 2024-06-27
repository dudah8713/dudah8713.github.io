---
title: "Unreal 5 hairstrandscore 모듈 사용하기"

categories: 
     - Unreal5
tags:
    - Game Dev, Unreal5
---

# Unreal 5 HairStrandsCore 모듈

> **Udemy의 Ultimate Game Developer 81번째 강의**

- HairStrandsCore 모듈을 .Build.cs의 PublicDependencyModuleNames에 추가 후에 GroomComponent를 사용하는 부분
1. 강의대로 따라 했더니 처음에는  GroomComponent.h에 아래의 헤더 파일이 없어서 오류가 발생
    
      `#include "NiagaraDataInterfacePhysicsAsset.h”` 
	  
→ PublicDependencyModuleNames에 “Niagara”도 추가 후에 프로젝트 파일 재생성 하니 해결
    
2. 그 다음에 .uproject 를 실행하려고 하니 아래와 같은 에러창을 띄우며 실행 불가능

🚧 게임 모듈을 로드하지 못했습니다. 운영체제 오류가 있거나 모듈 설정이 제대로 되지 않았을 수 있습니다.**

→ 엔진 버전업이 되면서 HairStrandsCore 모듈에 HairStrands 플러그인이 필요하다는 것을 알았다.

→ .uproject의 `"Plugins":` 부분에 아래와 같이 HairStrands 플러그인 사용 추가

```cpp
 "Plugins": [
        {
            "Name": "ModelingToolsEditorMode",
            "Enabled": true,
            "TargetAllowList": [
                "Editor"
            ]
        },
        {
            "Name": "HairStrands",
            "Enabled": true
        }       
    ]
```

→ C:\..\UE_5.4\Engine\Plugins\Runtime\HairStrands\HairStrands.uplugin 파일 아래와 같이 수정

```cpp

"EnabledByDefault": true,
```

→ 이후 다시 한번 프로젝트 파일 재생성 과정을 통해서 해결