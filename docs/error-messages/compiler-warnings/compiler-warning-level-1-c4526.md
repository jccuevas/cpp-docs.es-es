---
title: Advertencia del compilador (nivel 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 892e6c37e54a868be48ced35354a1096aa7bf9d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536733"
---
# <a name="compiler-warning-level-1-c4526"></a>Advertencia del compilador (nivel 1) C4526

'function': función miembro estática no puede invalidar la función virtual ' reemplazará la función virtual se ocultará

La función miembro estática cumple los criterios para invalidar la función virtual, lo que hace que la función miembro virtual y static.

El código siguiente genera la advertencia C4526:

```
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

Los siguientes son posibles soluciones:

- Si la función se ha diseñado para reemplazar la función virtual de clase base, quite el especificador estático.

- Si la función esté destinada a ser una función miembro estática, cambie el nombre por lo que no entra en conflicto con la función virtual de clase base.