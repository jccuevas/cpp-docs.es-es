---
title: Operadores de asignación de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a13f3b36ae4f5bbd11f170d78d735427882d2ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="c-assignment-operators"></a>Operadores de asignación de C
Una operación de asignación asigna el valor del operando derecho a la ubicación de almacenamiento designada por el operando izquierdo. Por consiguiente, el operando izquierdo de una operación de asignación debe ser un valor L modificable. Después de la asignación, una expresión de asignación tiene el valor del operando izquierdo, pero no es un valor L.  
  
 **Sintaxis**  
  
 *assignment-expression*:  
 *conditional-expression*  
  
 *unary-expression assignment-operator assignment-expression*  
  
 *assignment-operator*: uno de  
 **= \*=** `/=` `%=` `+=` **-= <\<= >>= &=** `^=` `|=`  
  
 Los operadores de asignación de C pueden transformar y asignar valores en una única operación. C proporciona los operadores de asignación siguientes:  
  
|Operador|Operación realizada|  
|--------------|-------------------------|  
|**=**|Asignación simple|  
|**\*=**|Asignación y multiplicación|  
|`/=`|Asignación y división|  
|`%=`|Asignación y resto|  
|`+=`|Asignación y suma|  
|**-=**|Asignación y resta|  
|**<\<=**|Asignación y desplazamiento a la izquierda|  
|**>>=**|Asignación y desplazamiento a la derecha|  
|**&=**|Asignación AND bit a bit|  
|`^=`|Asignación OR exclusivo bit a bit|  
|`&#124;=`|Asignación OR inclusivo bit a bit|  
  
 En la asignación, el tipo del valor derecho se convierte al tipo del valor izquierdo, y el valor se almacena en el operando izquierdo después de que haya ocurrido la asignación. El operando izquierdo no debe ser una matriz, función o constante. La ruta de acceso específica de la conversión, que depende de los dos tipos, se describe con detalle en [Conversiones de tipos](../c-language/type-conversions-c.md).  
  
## <a name="see-also"></a>Vea también  
 [Operadores de asignación](../cpp/assignment-operators.md)