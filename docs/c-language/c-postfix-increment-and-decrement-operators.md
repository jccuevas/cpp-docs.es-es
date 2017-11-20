---
title: Operadores de incremento y decremento postfijos de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6279ede332ffbcc12db4f8c72e17fe9050cc96e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operadores de incremento y decremento postfijos de C
Los operandos de los operadores de incremento y decremento de postfijo son tipos escalares que son valores L modificables.  
  
## <a name="syntax"></a>Sintaxis  
 *postfix-expression*:  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 El resultado de la operación de incremento y decremento de postfijo es el valor del operando. Una vez obtenido el resultado, se incrementa (o se reduce) el valor del operando. En el código siguiente se muestra el operador de incremento de postfijo.  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 En este ejemplo, la variable `var` se compara con 0 y luego se incrementa. Si `var` era positivo antes de que se incrementara, se ejecuta la siguiente instrucción. En primer lugar, se asigna el valor del objeto indicado por `q` al objeto indicado por `p`. A continuación, se incrementan `q` y `p`.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de incremento y decremento postfijos: ++ y --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)