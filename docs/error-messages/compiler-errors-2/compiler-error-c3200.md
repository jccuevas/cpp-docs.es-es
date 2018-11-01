---
title: Error del compilador C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7eb0c00f4f4c5c59766bf305acfef89e12a6cfb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505071"
---
# <a name="compiler-error-c3200"></a>Error del compilador C3200

'template': argumento de plantilla no válido para el parámetro de plantilla 'parámetro'; se esperaba una plantilla de clase

Se pasó un argumento no válido a una plantilla de clase. La plantilla de clase espera una plantilla como un parámetro. En el ejemplo siguiente, una llamada a `Y<int, int> aY` generará C3200. El primer parámetro debe ser una plantilla, como `Y<X, int> aY`.

```
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```