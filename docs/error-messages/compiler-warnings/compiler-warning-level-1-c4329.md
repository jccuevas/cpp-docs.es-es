---
title: Advertencia del compilador (nivel 1) C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: 31ea3aec2c7dd8e02a23a5c3cf6e5ac406636516
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622591"
---
# <a name="compiler-warning-level-1-c4329"></a>Advertencia del compilador (nivel 1) C4329

__declspec(Align()) se omite en la enumeración

El uso de la [alinear](../../cpp/align-cpp.md) palabra clave de la [__declspec](../../cpp/declspec.md) no se permite un modificador en un `enum`. El ejemplo siguiente genera C4329:

```
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```