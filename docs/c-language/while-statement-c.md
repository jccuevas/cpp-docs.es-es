---
title: "while (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- while
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e383ae0646bdf15c38f6537de0adec9bb9468486
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="while-statement-c"></a>while (Instrucción) (C)
La instrucción `while` permite repetir una instrucción hasta que una expresión especificada sea false.  
  
## <a name="syntax"></a>Sintaxis  
 *iteration-statement*:  
 **while (**  *expression*  **)**  *statement*  
  
 *expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:  
  
1.  Se evalúa *expression*.  
  
2.  Si *expression* es inicialmente false, el cuerpo de la instrucción `while` nunca se ejecuta y el control pasa de la instrucción `while` a la siguiente instrucción del programa.  
  
     Si *expression* es true (distinta de cero), el cuerpo de la instrucción se ejecuta y se repite el proceso a partir del paso 1.  
  
 La instrucción `while` también puede finalizar cuando se ejecuta **break**, `goto` o `return` dentro del cuerpo de la instrucción. Use la instrucción **continue** para finalizar una iteración sin salir del bucle `while`. La instrucción **continue** pasa el control a la siguiente iteración de la instrucción `while`.  
  
 Este es un ejemplo de la instrucción `while`:  
  
```  
while ( i >= 0 )   
{  
    string1[i] = string2[i];  
    i--;  
}  
```  
  
 En este ejemplo se copian caracteres de `string2` a `string1`. Si `i` es mayor o igual que 0, `string2[i]` se asigna a `string1[i]` y `i` se reduce. Cuando `i` alcanza o desciende por debajo de 0, la ejecución de la instrucción `while` finaliza.  
  
## <a name="see-also"></a>Vea también  
 [while (Instrucción) (C++)](../cpp/while-statement-cpp.md)
