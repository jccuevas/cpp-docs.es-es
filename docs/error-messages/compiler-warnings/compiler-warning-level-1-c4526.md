---
title: Advertencia del compilador (nivel 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: d4d772f3e505979a6ea5c3e7923fefa621601370
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186509"
---
# <a name="compiler-warning-level-1-c4526"></a>Advertencia del compilador (nivel 1) C4526

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
