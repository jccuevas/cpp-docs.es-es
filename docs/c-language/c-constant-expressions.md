---
title: Expresiones constantes de C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490537"
---
# <a name="c-constant-expressions"></a>Expresiones constantes de C

Una expresión constante se evalúa en tiempo de compilación, no en tiempo de ejecución y se puede usar en cualquier lugar en el que se pueda usar una constante. La expresión constante se debe evaluar como una constante que se encuentre en el intervalo de valores representables para ese tipo. Los operandos de una expresión constante pueden ser constantes enteras, constantes de caracteres, constantes de punto flotante, constantes de enumeración, conversiones de tipo, expresiones **sizeof** y otras expresiones constantes.

## <a name="syntax"></a>Sintaxis

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression* **?** *expression* **:** *conditional-expression*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator*: uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Los elementos no terminales para declarador de struct, enumerador, declarador directo, declarador directo-abstracto e instrucción etiquetada contienen el elemento no terminal *constant-expression*.

Se debe usar una expresión constante entera para especificar el tamaño de un miembro de campo de bits de una estructura, el valor de una constante de enumeración, el tamaño de una matriz o el valor de una constante **case**.

Las expresiones constantes usadas en las directivas de preprocesador están sujetas a restricciones adicionales. Por consiguiente, se conocen como “expresiones constantes restringidas”. Una expresión constante restringida no puede contener expresiones **sizeof**, constantes de enumeración, conversiones de tipos a cualquier tipo ni constantes de tipo flotante. Puede, en cambio, contener la expresión constante especial **defined (** _identifier_ **)**.

## <a name="see-also"></a>Vea también

- [Operandos y expresiones](../c-language/operands-and-expressions.md)
