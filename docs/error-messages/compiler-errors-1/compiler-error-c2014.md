---
title: Error del compilador C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757402"
---
# <a name="compiler-error-c2014"></a>Error del compilador C2014

el comando de preprocesador debe iniciarse como primer espacio que no esté en blanco

El signo de `#` de una directiva de preprocesador debe ser el primer carácter de una línea que no sea un espacio en blanco.

En el ejemplo siguiente se genera C2014:

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Solución posible:

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
