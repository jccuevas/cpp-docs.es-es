---
title: Error del compilador C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662923"
---
# <a name="compiler-error-c2619"></a>Error del compilador C2619

'identifier%$S': no se permite un miembro de datos estático en un struct o unión anónimo

Se declara `static` un miembro anónimo de un struct o unión.

El ejemplo siguiente genera el error C2619 y muestra cómo corregirlo eliminando la palabra clave static.

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```