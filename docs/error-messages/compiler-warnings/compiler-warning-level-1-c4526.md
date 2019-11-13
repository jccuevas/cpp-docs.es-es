---
title: ADVERTENCIA del compilador (nivel 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 60ac01d6a118f37a22b39ab41fa60252866f3360
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966272"
---
# <a name="compiler-warning-level-1-c4526"></a>ADVERTENCIA del compilador (nivel 1) C4526

' función ': la función miembro estática no puede invalidar la función virtual ' function'override omitida; la función virtual se ocultará

La función miembro estática cumple los criterios para invalidar la función virtual, que hace que la función miembro sea virtual y estática.

El código siguiente genera C4526:

```cpp
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

A continuación se indican las posibles correcciones:

- Si la función estaba pensada para invalidar la función virtual de clase base, quite el especificador estático.

- Si la función estaba diseñada para ser una función miembro estática, cambie su nombre para que no entre en conflicto con la función virtual de la clase base.