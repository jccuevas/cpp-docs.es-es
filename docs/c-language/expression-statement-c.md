---
title: "Expression (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7438899eb9c1c2f17b4e74c859d454e2b69af600
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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