---
title: "Asignación compuesta de C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b8b9166c1beae167f6d31913c3df10a8f57bbef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-compound-assignment"></a>Asignación compuesta de C
Los operadores de asignación compuesta combinan el operador de la asignación simple con otro operador binario. Los operadores de asignación compuesta realizan la operación especificada por el operador adicional y, a continuación, asignan el resultado al operando izquierdo. Por ejemplo, una expresión de asignación compuesta tal como  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 puede entenderse como  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 En cambio, la expresión de asignación compuesta no es equivalente a la versión expandida porque la expresión de asignación compuesta evalúa *expression1* una sola vez, mientras que la versión expandida evalúa *expression1* dos veces: en la operación de suma y en la operación de asignación.  
  
 Los operandos de un operador de asignación compuesta deben ser de tipo entero o flotante. Cada operador de asignación compuesta realiza las conversiones que realiza el operador binario correspondiente y restringe los tipos de sus operandos en consecuencia. Los operadores de suma y asignación (`+=`) y resta y asignación (**-=**) también pueden tener un operando izquierdo de tipo de puntero, en cuyo caso el operando derecho debe ser de tipo entero. El resultado de una operación de asignación compuesta tiene el valor y el tipo del operando izquierdo.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 En este ejemplo, se realiza una operación AND inclusiva bit a bit en `n` y `MASK` y el resultado se asigna a `n`. La constante de manifiesto `MASK` se define con una directiva de preprocesador [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Operadores de asignación de C](../c-language/c-assignment-operators.md)