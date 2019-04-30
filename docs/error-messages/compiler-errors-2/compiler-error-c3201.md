---
title: Error del compilador C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 92e068103563f7427de7b394536e72b06fab3374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402767"
---
# <a name="compiler-error-c3201"></a>Error del compilador C3201

la lista de parámetros de plantilla de la plantilla de clase 'template' no coincide con la lista de parámetros de plantilla del parámetro de plantilla 'template'

Se pasó una plantilla de clase en el argumento a una plantilla de clase que no toma un parámetro de plantilla o se pasó un número de argumentos de plantilla para el argumento de plantilla predeterminado que no coinciden.

```
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```