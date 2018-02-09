---
title: Constantes de tipo entero de C | Microsoft Docs
ms.custom: 
ms.date: 02/01/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c23e90d235e1ad2a8cca577c5cfbf2be55b52b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-constants"></a>Constantes de tipo entero de C

Una "constante de tipo entero" es un número decimal (base 10), octal (base 8) o hexadecimal (base 16) que representa un valor de tipo entero. Utilice las constantes de tipo entero para representar valores de tipo entero que no se pueden modificar.

## <a name="syntax"></a>Sintaxis

*integer-constant*:  
&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>  

*decimal-constant*:  
&nbsp;&nbsp;*nonzero-digit*  
&nbsp;&nbsp;*decimal-constant* *digit*  

*octal-constant*:  
&nbsp;&nbsp;**0**  
&nbsp;&nbsp;*octal-constant* *octal-digit*  

*hexadecimal-constant*:  
&nbsp;&nbsp;**0x**  *hexadecimal-digit*  
&nbsp;&nbsp;**0X**  *hexadecimal-digit*  
&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*  

*nonzero-digit*: uno de  
&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**  

*octal-digit*: uno de  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7**  

*hexadecimal-digit*: uno de  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;**a b c d e f**  
&nbsp;&nbsp;**A B C D E F**  
  
*integer-suffix*:  
&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<sub>opt</sub>

*unsigned-suffix*: uno de  
&nbsp;&nbsp;**u U**  

*long-suffix*: uno de  
&nbsp;&nbsp;**l L**  
  
*64-bit-integer-suffix*: uno de &nbsp;&nbsp;**i64 I64**  

Las constantes de tipo entero son positivas a menos que vayan precedidas de un signo menos (**-**). El signo menos se interpreta como el operador aritmético unario de negación. (Vea [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md) para obtener información sobre este operador).

Si una constante entera comienza con **0x** o **0X**, es hexadecimal. Si empieza con el dígito **0**, es octal. En los demás casos, se supone que es decimal.

Las líneas siguientes son equivalentes:

```C
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Los dígitos de una constante de tipo entero no se pueden separar con ningún carácter de espacio en blanco. En estos ejemplos se muestran constantes decimales, octales y hexadecimales válidas.

```C
/* Decimal Constants */
10
132
32179

/* Octal Constants */
012
0204
076663

/* Hexadecimal Constants */
0xa or 0xA
0x84
0x7dB3 or 0X7DB3
```

## <a name="see-also"></a>Vea también

[Constantes de C](../c-language/c-constants.md)  
