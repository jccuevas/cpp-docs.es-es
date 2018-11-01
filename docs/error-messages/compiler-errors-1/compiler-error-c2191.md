---
title: Error del compilador C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: 23dfe1d95ab75f253fc2a7b4b00dfcd1aaaa3bbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623527"
---
# <a name="compiler-error-c2191"></a>Error del compilador C2191

segunda lista de parámetros más larga que la primera

Una función de C se ha declarado una segunda vez con una lista de parámetros más larga. C no admite funciones sobrecargadas.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2191:

```
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```