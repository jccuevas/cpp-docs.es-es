---
title: Compilador advertencia (nivel 4) C4706 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: d4f4edcbf4a4cb147c2acb8e6cb530a4a0f9a9a9
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4706"></a>Advertencia del compilador (nivel 4) C4706
asignación en la expresión condicional  
  
 El valor de prueba en una expresión condicional era el resultado de una asignación.  
  
 Una asignación tiene un valor (el valor en el lado izquierdo de la asignación) que puede utilizarse correctamente en otra expresión, incluida una expresión de prueba.  
  
 El ejemplo siguiente genera C4706:  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 Esta advertencia se producirá si se doblan los paréntesis alrededor de la condición de prueba:  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 Si su intención es probar una relación y no desea realizar una asignación, utilice la `==` operador. Por ejemplo, la línea siguiente prueba si un y b son iguales:  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 Si piensa realizar la prueba del resultado de una asignación, una prueba para asegurarse de que la asignación es distinto de cero o no null. Por ejemplo, el siguiente código no generará esta advertencia:  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```
