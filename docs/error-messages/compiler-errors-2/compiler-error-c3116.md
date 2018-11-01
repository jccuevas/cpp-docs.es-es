---
title: Error del compilador C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: 3f587bc677d64bda0fb5eea0b7ebc8d5761a2e75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612028"
---
# <a name="compiler-error-c3116"></a>Error del compilador C3116

'especificador de almacenamiento': clase de almacenamiento no es válida para el método de interfaz

Ha utilizado `typedef`, `register`, o `static` como la clase de almacenamiento para un método de interfaz. Estas clases de almacenamiento no se permiten en los miembros de interfaz.

El ejemplo siguiente genera C3116:

```
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```