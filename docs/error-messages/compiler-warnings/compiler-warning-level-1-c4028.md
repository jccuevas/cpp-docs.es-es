---
title: Compilador advertencia (nivel 1) C4028 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4028
dev_langs:
- C++
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b6c71f04b8f0829bbc321d38a18e4307df51ff0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054745"
---
# <a name="compiler-warning-level-1-c4028"></a>Compilador advertencia (nivel 1) C4028

'número' distinto de la declaración de parámetros formales

El tipo del parámetro formal no coincide con el parámetro correspondiente en la declaración. Se utiliza el tipo en la declaración original.

Esta advertencia sólo es válida para el código fuente de C.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4028.

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```