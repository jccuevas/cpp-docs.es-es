---
title: Error de compilador C3202
ms.date: 11/04/2016
f1_keywords:
- C3202
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
ms.openlocfilehash: 4c0ab49e94c2e4e001f394a3394935a8085cbddb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738731"
---
# <a name="compiler-error-c3202"></a>Error de compilador C3202

'nombre argumento' : argumento predeterminado no válido para el parámetro de plantilla 'parámetro'; se esperaba una plantilla de clase.

Se pasó un argumento predeterminado no válido para un parámetro de plantilla.

El ejemplo siguiente genera la advertencia C3202:

```cpp
// C3202.cpp
template<typename T>
class X
{
};

class Z
{
};

template<template<typename U> class T1 = Z, typename T2> // C3202
class Y
{
};
```
