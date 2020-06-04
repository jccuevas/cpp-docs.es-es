---
title: Operadores de asignación de C
ms.date: 06/14/2018
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
ms.openlocfilehash: e8ada96daaec249a05882aceae9b7d9e86b92065
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168804"
---
# <a name="c-assignment-operators"></a>Operadores de asignación de C

Una operación de asignación asigna el valor del operando derecho a la ubicación de almacenamiento designada por el operando izquierdo. Por consiguiente, el operando izquierdo de una operación de asignación debe ser un valor L modificable. Después de la asignación, una expresión de asignación tiene el valor del operando izquierdo, pero no es un valor L.

## <a name="syntax"></a>Sintaxis

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator*: uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **\*=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **|=**

Los operadores de asignación de C pueden transformar y asignar valores en una única operación. C proporciona los operadores de asignación siguientes:

|Operador|Operación realizada|
|--------------|-------------------------|
|**=**|Asignación simple|
|**&#42;=**|Asignación y multiplicación|
|**/=**|Asignación y división|
|**%=**|Asignación y resto|
|**+=**|Asignación y suma|
|**-=**|Asignación y resta|
|**<\<=**|Asignación y desplazamiento a la izquierda|
|**>>=**|Asignación y desplazamiento a la derecha|
|**&=**|Asignación AND bit a bit|
|**^=**|Asignación OR exclusivo bit a bit|
|**&#124;=**|Asignación OR inclusivo bit a bit|

En la asignación, el tipo del valor derecho se convierte al tipo del valor izquierdo, y el valor se almacena en el operando izquierdo después de que haya ocurrido la asignación. El operando izquierdo no debe ser una matriz, función o constante. La ruta de acceso específica de la conversión, que depende de los dos tipos, se describe con detalle en [Conversiones de tipos](../c-language/type-conversions-c.md).

## <a name="see-also"></a>Vea también

- [Operadores de asignación](../cpp/assignment-operators.md)
