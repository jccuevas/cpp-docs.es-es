---
title: Error del compilador C3874
ms.date: 11/04/2016
f1_keywords:
- C3874
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
ms.openlocfilehash: 73476d50b6cfe098ee9d8084837c2090e198a6cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242908"
---
# <a name="compiler-error-c3874"></a>Error del compilador C3874

tipo de valor devuelto de 'function' debe ser 'int' en lugar de 'type'

Una función no tiene el tipo de valor devuelto que el compilador esperaba.

El ejemplo siguiente genera C3874:

```
// C3874b.cpp
double main()
{   // C3874
}
```