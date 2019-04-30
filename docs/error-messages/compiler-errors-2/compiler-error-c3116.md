---
title: Error del compilador C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: 3f587bc677d64bda0fb5eea0b7ebc8d5761a2e75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376073"
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