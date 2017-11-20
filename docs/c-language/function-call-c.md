---
title: "Llamada de función (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0faf339877b075a1337c73ec5ca3c41a869ceec2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-c"></a>Llamada de función (C)
Una “llamada a función” es una expresión que incluye el nombre de la función que se llama o el valor de un puntero a función y, opcionalmente, los argumentos que se pasan a la función.  
  
## <a name="syntax"></a>Sintaxis  
 *postfix-expression*:  
 *postfix-expression*  **(**  *argument-expression-list* opt**)**  
  
 *argument-expression-list*:  
 *assignment-expression*  
  
 *argument-expression-list*  **,**  *assignment-expression*  
  
 El elemento *postfix-expression* se debe evaluar como una dirección de función (por ejemplo, un identificador de función o el valor de un puntero de función) y el elemento *argument-expression-list* es una lista de expresiones (separadas por comas) cuyos valores (los "argumentos") se pasan a la función. El elemento *argument-expression-list* puede estar vacío.  
  
 Una expresión de llamada a función tiene el valor y el tipo del valor devuelto de la función. Una función no puede devolver un objeto de tipo de matriz. Si el tipo de valor devuelto de la función es `void` (es decir, la función nunca se ha declarado para devolver un valor), la expresión de llamada a función también tiene el tipo `void`. (Vea [Llamadas a función](../c-language/function-calls.md) para obtener más información).  
  
## <a name="see-also"></a>Vea también  
 [Operador de llamada de función: ()](../cpp/function-call-operator-parens.md)