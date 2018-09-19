---
title: Error del compilador C2586 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2586
dev_langs:
- C++
helpviewer_keywords:
- C2586
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a85097f6383ddb788e1278aebf4732591fd38ec2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060416"
---
# <a name="compiler-error-c2586"></a>Error del compilador C2586

sintaxis de conversión definido por el usuario incorrecta: direccionamientos indirectos no válidos

No se permite el direccionamiento indirecto de un operador de conversión.

El ejemplo siguiente genera C2586:

```
// c2586.cpp
// compile with: /c
struct C {
   * operator int();   // C2586
   operator char();   // OK
};
```