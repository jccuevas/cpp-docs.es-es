---
title: Compilador advertencia (nivel 4) C4706 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4706
dev_langs: C++
helpviewer_keywords: C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 824028fb7fd6d563a7f49017eb6b35d1443490bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 Esta advertencia se producirá si se doblan los paréntesis que rodean la condición de prueba:  
  
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
  
 Si va a hacer la prueba de valor el resultado de una asignación, se prueba para asegurarse de que la asignación es distinto de cero o no es null. Por ejemplo, el siguiente código no generará esta advertencia:  
  
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