---
title: Error del compilador C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 7c16ffa37f4d7192956afae26c825b63add1bfdd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540258"
---
# <a name="compiler-error-c3412"></a>Error del compilador C3412

'template': no se puede especializar la plantilla en el ámbito actual

No se puede especializar una plantilla en el ámbito de clase, solo en global o de espacio de nombres.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3412.

```
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra una posible solución.

```
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```