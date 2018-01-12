---
title: Compilador advertencia (nivel 4) C4130 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4130
dev_langs: C++
helpviewer_keywords: C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 282f9755470baca115d0595b002b929874619a93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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