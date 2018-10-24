---
title: Operadores de adición de C | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 339904e3fe75c712254f3a7802fc76a0e283c8e5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808360"
---
# <a name="c-additive-operators"></a>Operadores de adición de C

Los operadores aditivos realizan la suma (**+**) y la resta (**-**).

## <a name="syntax"></a>Sintaxis

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicative-expression*

> [!NOTE]
> Aunque la sintaxis de *additive-expression* incluye *multiplicative-expression*, no implica que se necesiten expresiones que usen la multiplicación. Vea la sintaxis de *multiplicative-expression*, *cast-expression* y *unary-expression* en el [Resumen de la sintaxis del lenguaje C](../c-language/c-language-syntax-summary.md).

Los operandos pueden ser valores enteros o de punto flotante. Algunas operaciones aditivas también se pueden realizar sobre valores de puntero, como se explica en la descripción de cada operador.

Los operadores aditivos realizan las conversiones aritméticas habituales sobre operandos enteros y de punto flotante. El tipo del resultado es el tipo de los operandos después de la conversión. Como las conversiones realizadas por los operadores aditivos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación aditiva no se puede representar en el tipo de los operandos después de la conversión.

## <a name="see-also"></a>Vea también

[Operadores de adición: + y -](../cpp/additive-operators-plus-and.md)