---
title: Operadores bit a bit de C | Microsoft Docs
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
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
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
ms.openlocfilehash: 620177616e8b60d910d064d7c345633ac5155020
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="c-bitwise-operators"></a>Operadores bit a bit de C
Los operadores bit a bit realizan operaciones AND bit a bit (**&**), OR exclusivo bit a bit (**^**) y OR inclusivo bit a bit (**&#124;**).  
  
 **Sintaxis**  
  
 *AND-expression*:  
 *equality-expression*  
  
 *AND-expression*  **&**  *equality-expression*  
  
 *exclusive-OR-expression*:  
 *AND-expression*  
  
 *exclusive-OR-expression*  **^**  *AND-expression*  
  
 *inclusive-OR-expression*:  
 *exclusive-OR-expression*  
  
 *inclusive-OR-expression* &#124; *exclusive-OR-expression*  
  
 Los operandos de los operadores bit a bit deben tener tipos enteros, pero sus tipos pueden ser diferentes. Estos operadores realizan las conversiones aritméticas habituales; el tipo del resultado es el tipo de los operandos después de la conversión.  
  
 A continuación se describen los operadores bit a bit de C:  
  
|Operador|Descripción|  
|--------------|-----------------|  
|**&**|El operador AND bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si ambos bits son 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|  
|**^**|El operador OR exclusivo bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si un bit es 0 y el otro bit es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|  
|**&#124;**|El operador OR inclusivo bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si uno de los dos bits es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|  
  
## <a name="examples"></a>Ejemplos  
 Estas declaraciones se utilizan para los tres ejemplos siguientes:  
  
```  
short i = 0xAB00;  
short j = 0xABCD;  
short n;  
  
n = i & j;  
```  
  
 El resultado asignado a `n` en este primer ejemplo es igual a `i` (0xAB00 hexadecimal).  
  
```  
n = i | j;  
  
n = i ^ j;  
```  
  
 El operador OR inclusivo bit a bit del segundo ejemplo produce el valor 0xABCD (hexadecimal), mientras que el operador OR exclusivo bit a bit del tercer ejemplo genera 0xCD (hexadecimal).  
  
 **Específicos de Microsoft**  
  
 Los resultados de la operación bit a bit en enteros con signo se definen en la implementación según el estándar de ANSI C. Para el compilador de Microsoft C, las operaciones bit a bit en enteros con signo funcionan igual que las operaciones bit a bit en enteros sin signo. Por ejemplo, `-16 & 99` puede expresarse en formato binario como  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 El resultado de la operación AND bit a bit es 96 (decimal).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Operador AND bit a bit: &](../cpp/bitwise-and-operator-amp.md)   
 [Operador OR exclusivo bit a bit:: ^](../cpp/bitwise-exclusive-or-operator-hat.md)   
 [Operador OR inclusivo bit a bit: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
