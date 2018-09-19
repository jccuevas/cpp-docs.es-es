---
title: Error del compilador C3116 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3116
dev_langs:
- C++
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1104b731fa565991615eb88cc34fa946e2bfb505
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077856"
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