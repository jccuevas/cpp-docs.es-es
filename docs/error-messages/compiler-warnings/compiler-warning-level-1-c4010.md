---
title: Compilador advertencia (nivel 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386556"
---
# <a name="compiler-warning-level-1-c4010"></a>Compilador advertencia (nivel 1) C4010

comentario de una línea contiene el carácter de continuación de línea

Un comentario de una línea, que se introdujo por / /, contiene una barra diagonal inversa (\\) que actúa como un carácter de continuación de línea. El compilador considera que la siguiente línea como continuación y lo trata como un comentario.

Algunas sintaxis dirigido al editores no indican la línea que sigue al carácter de continuación como un comentario. Omitir los colores en las líneas que causan esta advertencia de sintaxis.

El ejemplo siguiente genera C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```