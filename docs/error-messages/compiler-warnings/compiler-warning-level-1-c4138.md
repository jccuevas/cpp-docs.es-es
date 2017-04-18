---
title: Compilador advertencia (nivel 1) C4138 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 3f3009b5a4d8fd7c3810b8039e04f99c7eb9d6cc
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4138"></a>Advertencia del compilador (nivel 1) C4138
'*/' se encontró fuera del comentario  
  
 El delimitador de comentario de cierre no está precedido de un delimitador de comentario de apertura. El compilador supone que hay un espacio entre el asterisco (**\***) y la barra diagonal (/).  
  
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
