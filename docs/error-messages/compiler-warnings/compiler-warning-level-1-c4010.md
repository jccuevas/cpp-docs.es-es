---
title: Compilador advertencia (nivel 1) C4010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073109"
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