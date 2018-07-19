---
title: Operadores de incremento y decremento postfijos de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f96c48a69f692c8646de5dec8ad8e6431fb63c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381527"
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