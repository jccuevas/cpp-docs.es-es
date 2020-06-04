---
title: ADVERTENCIA del compilador (nivel 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 6045d49ee34f837ad9f22bac5b2b43b75a998f7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164695"
---
# <a name="compiler-warning-level-1-c4010"></a>ADVERTENCIA del compilador (nivel 1) C4010

el comentario de una sola línea contiene un carácter de continuación de línea

Un Comentario de una sola línea, que se introduce mediante//, contiene una barra diagonal inversa (\\) que actúa como un carácter de continuación de línea. El compilador considera que la siguiente línea es una continuación y la trata como un comentario.

Algunos editores orientados a la sintaxis no indican la línea que sigue al carácter de continuación como comentario. Omitir el color de la sintaxis en las líneas que causan esta advertencia.

En el ejemplo siguiente se genera C4010:

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
