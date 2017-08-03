---
title: "Expression (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: 8
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
ms.openlocfilehash: ed9c2524c015faaf2aff4467e68d32c01bc31d61
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="expression-statement-c"></a>Expression (Instrucción) (C)
Cuando se ejecuta una instrucción de expresión, la expresión se evalúa según las reglas descritas en [Expresiones y asignaciones](../c-language/expressions-and-assignments.md).  
  
## <a name="syntax"></a>Sintaxis  
 *expression-statement*:  
 *expression* opt**;**  
  
 Todos los efectos secundarios de la evaluación de la expresión se completan antes de que se ejecute la instrucción siguiente. Una instrucción de expresión vacía se conoce como instrucción nula. Para obtener más información, vea [La instrucción Null](../c-language/null-statement-c.md).  
  
 En estos ejemplos se muestran instrucciones de expresión.  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 En la última instrucción, la expresión de llamada de función, el valor de la expresión, que incluye cualquier valor devuelto por la función, se incrementa en 3 y, a continuación, se asigna a las variables `y` y `z`.  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones](../c-language/statements-c.md)
