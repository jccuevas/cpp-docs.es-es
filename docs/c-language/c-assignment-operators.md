---
title: "Operadores de asignación de C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d510973a7b7c12185f5cde32a49af3537a436c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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