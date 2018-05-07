---
title: Compilador advertencia (nivel 1) C4010 | Documentos de Microsoft
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
ms.openlocfilehash: 06ab6307a34887fe2d8a8719e20c31da9728664b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4010"></a>Compilador advertencia (nivel 1) C4010
comentario de una línea contiene el carácter de continuación de línea  
  
 Un comentario de línea, que se introdujo por / /, contiene una barra diagonal inversa (\\) que actúa como un carácter de continuación de línea. El compilador considera que la línea siguiente para tener una continuación y lo trata como un comentario.  
  
 Algunas sintaxis dirigen editores no indican la línea que sigue al carácter de continuación como un comentario. Omitir los colores en las líneas que causan esta advertencia de sintaxis.  
  
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