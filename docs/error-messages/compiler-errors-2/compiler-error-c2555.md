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
ms.openlocfilehash: 8f91ec33db2d3a7b6772556233a3c99b501ede76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017344"
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

Para obtener más información sobre el error C2555, consulte el artículo de Knowledge Base Q240862.

El ejemplo siguiente genera C2555:

```
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