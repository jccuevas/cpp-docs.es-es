---
title: Compilador advertencia (nivel 1) C4138 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc3102f18021c16663bdf61dcde6df5e6893d46c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197093"
---
# <a name="compiler-warning-level-1-c4138"></a>Advertencia del compilador (nivel 1) C4138
'*/' se encontró fuera del comentario  
  
 El delimitador de comentario de cierre no está precedido de un delimitador de comentario de apertura. El compilador supone un espacio entre el asterisco (<strong>\*</strong>) y la barra diagonal (/).  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 Esta advertencia puede producirse en un intento de anidar comentarios.  
  
 Esta advertencia puede evitarse si convierte en comentario las secciones de código que contienen comentarios, incluye el código en un bloque **#if/#endif** y establece la expresión de control en cero:  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```