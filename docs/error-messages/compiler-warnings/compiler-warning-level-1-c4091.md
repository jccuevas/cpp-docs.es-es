---
title: Del compilador (nivel 1) la advertencia C4091 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8fd377ed8b1f6425f0a1c13a83531fca1b797f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114103"
---
# <a name="compiler-warning-level-1-c4091"></a>Del compilador (nivel 1) la advertencia C4091

'keyword': omitido a la izquierda de 'tipo' cuando no se declara ninguna variable

El compilador detectó una situación donde el usuario probablemente diseñado una variable que se declara, pero el compilador no pudo declarar la variable.

## <a name="example"></a>Ejemplo

Un `__declspec` atributo al principio de una declaración de tipo definido por el usuario se aplica a la variable de ese tipo. C4091 indica que no hay ninguna variable se declara. El ejemplo siguiente genera la advertencia C4091.

```
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>Ejemplo

Si un identificador es una definición de tipo, no puede ser un nombre de variable. El ejemplo siguiente genera la advertencia C4091.

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```