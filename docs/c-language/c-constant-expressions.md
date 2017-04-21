---
title: Expresiones constantes de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0e3323c85ce7668adfe5b4a297ac8bab930c3ae6
ms.lasthandoff: 04/01/2017

---
# <a name="c-constant-expressions"></a>Expresiones constantes de C
Una expresión constante se evalúa en tiempo de compilación, no en tiempo de ejecución y se puede usar en cualquier lugar en el que se pueda usar una constante. La expresión constante se debe evaluar como una constante que se encuentre en el intervalo de valores representables para ese tipo. Los operandos de una expresión constante pueden ser constantes enteras, constantes de caracteres, constantes de punto flotante, constantes de enumeración, conversiones de tipo, expresiones `sizeof` y otras expresiones constantes.  
  
## <a name="syntax"></a>Sintaxis  
 *constant-expression*:  
 *conditional-expression*  
  
 *conditional-expression*:  
 *logical-OR-expression*  
  
 *logical-OR-expression* **?**  *expression* **:**  *conditional-expression*  
  
 *expression*:  
 *assignment-expression*  
  
 *expression* **,**  *assignment-expression*  
  
 *assignment-expression*:  
 *conditional-expression*  
  
 *unary-expression assignment-operator assignment-expression*  
  
 *assignment-operator*: uno de  
 **= \*= /= %= += -= <\<= >>= &= ^= &#124;=**  
  
 Los elementos no terminales para declarador de struct, enumerador, declarador directo, declarador directo-abstracto e instrucción etiquetada contienen el elemento no terminal *constant-expression*.  
  
 Se debe usar una expresión constante entera para especificar el tamaño de un miembro de campo de bits de una estructura, el valor de una constante de enumeración, el tamaño de una matriz o el valor de una constante **case**.  
  
 Las expresiones constantes usadas en las directivas de preprocesador están sujetas a restricciones adicionales. Por consiguiente, se conocen como “expresiones constantes restringidas”. Una expresión constante restringida no puede contener expresiones `sizeof`, constantes de enumeración, conversiones de tipos a cualquier tipo ni constantes de tipo flotante. Puede, en cambio, contener la expresión constante especial `defined (`*identifier*`)`.  
  
## <a name="see-also"></a>Vea también  
 [Operandos y expresiones](../c-language/operands-and-expressions.md)
