---
title: Error del compilador C2085 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082383"
---
# <a name="compiler-error-c2085"></a>Error del compilador C2085

'identifier': no en la lista de parámetros formales

El identificador se ha declarado en una definición de función, pero no en la lista de parámetros formales. (Sólo en ANSI C)

El ejemplo siguiente genera C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Posible resolución:

```
// C2085b.c
void func1( void );
int main( void ) {}
```

Con el punto y coma que falta, `func1()` parece una definición de función, no un prototipo, por lo que `main` se define dentro de `func1()`, Error C2085 para identificador `main`.