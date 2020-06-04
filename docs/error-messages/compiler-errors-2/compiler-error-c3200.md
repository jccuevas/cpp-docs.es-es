---
title: Error del compilador C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7f6b514231bcda18404e891e0acbe457c8f95146
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738783"
---
# <a name="compiler-error-c3200"></a>Error del compilador C3200

' plantilla ': argumento de plantilla no válido para el parámetro de plantilla ' parámetro '; se esperaba una plantilla de clase

Pasó un argumento no válido a una plantilla de clase. La plantilla de clase espera una plantilla como parámetro. En el ejemplo siguiente, al llamar a `Y<int, int> aY` se generará C3200. El primer parámetro debe ser una plantilla, como `Y<X, int> aY`.

```cpp
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
