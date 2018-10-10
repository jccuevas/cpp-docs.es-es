---
title: Error del compilador C2555 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0cd401aa1ee3611befb39d630f48f6aed36211c
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889951"
---
# <a name="compiler-error-c2555"></a>Error del compilador C2555

'clase1:: función1': función virtual de invalidación tipo devuelto es diferente y no es covariante de 'clase2:: función2'

Una función virtual y una función de reemplazo derivada tienen listas de parámetros idénticos, pero diferentes tipos de valor devuelto. Una función de reemplazo en una clase derivada no puede diferir de una función virtual en una clase base solo por su tipo de valor devuelto.

Para resolver este error, convierta el valor devuelto después de la función virtual se ha llamado.

También puede ver este error si se compila con/CLR.   Por ejemplo, el equivalente en Visual C++ a la siguiente declaración de C#:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

El ejemplo siguiente genera C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```