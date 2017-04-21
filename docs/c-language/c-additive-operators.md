---
title: "Operadores de adición de C | Microsoft Docs"
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
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 885967baa9a7e3651dde02bb5cfb1d6b9783f42b
ms.lasthandoff: 04/01/2017

---
# <a name="c-additive-operators"></a>Operadores de adición de C
Los operadores aditivos realizan la suma (**+**) y la resta (**-**).  
  
## <a name="syntax"></a>Sintaxis  
 *additive-expression*:  
 *multiplicative-expression*  
  
 *additive-expression*  **+**  *multiplicative-expression*  
  
 *additive-expression*  **-**  *multiplicative-expression*  
  
> [!NOTE]
>  Aunque la sintaxis de *additive-expression* incluye *multiplicative-expression*, no implica que se necesiten expresiones que usen la multiplicación. Vea la sintaxis de *multiplicative-expression*, *cast-expression* y *unary-expression* en el [Resumen de la sintaxis del lenguaje C](../c-language/c-language-syntax-summary.md).  
  
 Los operandos pueden ser valores enteros o de punto flotante. Algunas operaciones aditivas también se pueden realizar sobre valores de puntero, como se explica en la descripción de cada operador.  
  
 Los operadores aditivos realizan las conversiones aritméticas habituales sobre operandos enteros y de punto flotante. El tipo del resultado es el tipo de los operandos después de la conversión. Como las conversiones realizadas por los operadores aditivos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación aditiva no se puede representar en el tipo de los operandos después de la conversión.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición: + y -](../cpp/additive-operators-plus-and.md)
