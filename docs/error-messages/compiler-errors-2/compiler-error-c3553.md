---
title: Error del compilador C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 219592f2403904f9923e84bfd4539a22cddd02de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345462"
---
# <a name="compiler-error-c3553"></a>Error del compilador C3553

> decltype espera una expresión, no un tipo

La palabra clave `decltype()` requiere una expresión como argumento, no el nombre de un tipo. Por ejemplo, la última instrucción del siguiente fragmento de código genera el error C3553.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```