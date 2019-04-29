---
title: Error del compilador C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: b52797b945b1a652506b4a85171e60a91544bbf0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282834"
---
# <a name="compiler-error-c2190"></a>Error del compilador C2190

primera lista de parámetros más larga que la segunda

Una función de C se ha declarado una segunda vez con una lista de parámetros más corta. C no admite funciones sobrecargadas.

El ejemplo siguiente genera C2190:

```
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```