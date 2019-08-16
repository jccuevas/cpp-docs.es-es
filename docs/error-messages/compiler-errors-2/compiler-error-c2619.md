---
title: Error del compilador C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208433"
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