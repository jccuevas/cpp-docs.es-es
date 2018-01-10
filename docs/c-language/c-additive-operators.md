---
title: "Operadores de adición de C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 340aac3d3aab6951af43b824f1c8d0dd866f7a39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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