---
title: Compilador advertencia (nivel 4) C4130 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 32ec1055c5da769c026b778897a5bd9b741b2d40
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4130"></a>Advertencia del compilador (nivel 4) C4130
'operador': operación lógica en dirección de una constante de cadena.  
  
 Usar el operador con la dirección de un literal de cadena produce código inesperado.  
  
 El ejemplo siguiente genera la advertencia C4130:  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 La instrucción **if** compara el valor almacenado en el puntero `pc` con la dirección de la cadena "Hola", que se asigna por separado cada vez que aparece la cadena en el código. La instrucción **if** no compara la cadena a la que apunta `pc` con la cadena "Hola".  
  
 Para comparar cadenas, use la función `strcmp` .
