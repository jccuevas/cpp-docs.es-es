---
title: Error del compilador C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: a9c6465ef87c12135ad4e6709741f0027d8ea3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175152"
---
# <a name="compiler-error-c2150"></a>Error del compilador C2150

> '*identificador*': campo de bits debe tener el tipo 'int', 'signed int' o 'unsigned int'

El tipo base para un campo de bits debe ser `int`, `signed int`, o `unsigned int`.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo podría encontrar C2150 y cómo corregirlo:

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```