---
title: Compilador advertencia (nivel 4) C4125 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4125
dev_langs:
- C++
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7042dd8689bf5a9bafc35d6bdaa6028f0c52df2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087245"
---
# <a name="compiler-warning-level-4-c4125"></a>Advertencia del compilador (nivel 4) C4125

el dígito decimal finaliza la secuencia de escape octal

El compilador evalúa el número octal sin el dígito decimal y supone que el dígito decimal es un carácter.

## <a name="example"></a>Ejemplo

```
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

Si el dígito 9 está pensado como un carácter, corrija el ejemplo siguiente:

```
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```