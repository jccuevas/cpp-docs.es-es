---
title: "while (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: while
dev_langs: C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69f4dfa2feb48bf0fb8ea6f8fca90107c788137e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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