---
title: ADVERTENCIA del compilador (nivel 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: ce6dd980ef70f129a0dbae474b8f717f7573f861
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626752"
---
# <a name="compiler-warning-level-1-c4091"></a>ADVERTENCIA del compilador (nivel 1) C4091

' palabra clave ': se omite a la izquierda de ' tipo ' cuando no se declara ninguna variable

El compilador detectó una situación en la que el usuario probablemente pretendía que se declarara una variable, pero el compilador no podía declarar la variable.

## <a name="example"></a>Ejemplo

Un atributo `__declspec` al principio de una declaración de tipos definidos por el usuario se aplica a la variable de ese tipo. C4091 indica que no hay ninguna variable declarada. En el ejemplo siguiente se genera C4091.

```cpp
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

Si un identificador es una definición de tipo, no puede ser también un nombre de variable. En el ejemplo siguiente se genera C4091.

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```