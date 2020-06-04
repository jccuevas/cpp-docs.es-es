---
title: Advertencia del compilador (nivel 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e1f28f5afb1879229ff0d408cb576312966e1c81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200114"
---
# <a name="compiler-warning-level-1-c4138"></a>Advertencia del compilador (nivel 1) C4138

'*/' se encontró fuera del comentario

El delimitador de comentario de cierre no está precedido de un delimitador de comentario de apertura. El compilador supone que hay un espacio entre el asterisco (<strong>\*</strong>) y la barra diagonal (/).

## <a name="example"></a>Ejemplo

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Esta advertencia puede producirse en un intento de anidar comentarios.

Esta advertencia puede evitarse si convierte en comentario las secciones de código que contienen comentarios, incluye el código en un bloque **#if/#endif** y establece la expresión de control en cero:

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```
