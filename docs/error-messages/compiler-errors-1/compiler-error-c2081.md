---
title: Error del compilador C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2bccd15b8c2b6d1c5cd6c4b536bbdaf350eb0181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408659"
---
# <a name="compiler-error-c2081"></a>Error del compilador C2081

'identifier': nombre de no es válido de lista de parámetros formales

El identificador produjo un error de sintaxis.

Este error puede deberse a utilizando el estilo anterior de la lista de parámetros formales. Debe especificar el tipo de parámetros formales en la lista de parámetros formales.

El ejemplo siguiente genera C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Posible resolución:

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```