---
title: Error del compilador C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301995"
---
# <a name="compiler-error-c2081"></a>Error del compilador C2081

' Identifier ': el nombre de la lista de parámetros formales no es válido

El identificador causó un error de sintaxis.

Este error puede deberse al uso del estilo antiguo para la lista de parámetros formales. Debe especificar el tipo de parámetros formales en la lista de parámetros formales.

En el ejemplo siguiente se genera C2081:

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Solución posible:

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
