---
title: Advertencia del compilador (nivel 4) C4337
ms.date: 11/04/2016
f1_keywords:
- C4337
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
ms.openlocfilehash: f86d03e30e2776a8dae4cf56032c45d0022ca01d
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683308"
---
# <a name="compiler-warning-level-4-c4337"></a>Advertencia del compilador (nivel 4) C4337

la biblioteca de tipos a la que se hace referencia cruzada ' typelib1 ' en ' typelib2 ' se está importando automáticamente

El atributo auto_search de [la directiva #import](../../preprocessor/hash-import-directive-cpp.md) provocó la importación implícita de una biblioteca de tipos.

Dadas dos bibliotecas de tipos en el disco creadas a partir de los dos archivos siguientes (compilados con MIDL. exe):

```
// C4337a.idl
[
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)
]
library C4337aLib
{
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]
   enum E_C4337a
   {
      one = 0,
      two = 1,
      three = 2
    };
};
```

y, a continuación, el segundo archivo. idl,

```
// C4337b.idl
[
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)
]

library C4337bLib
{
   importlib("c4337a.tlb");

   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]
   struct S_C4337b
   {
      enum E_C4337a e;
   };
};
```

En el ejemplo siguiente se genera C4337:

```cpp
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```