---
title: Operadores de postfijo
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: 45f7b67b62657c498bdd9ebcf5d85379cdcdd211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440709"
---
# <a name="postfix-operators"></a>Operadores de postfijo

Los operadores de postfijo tienen la máxima prioridad (el enlace más estricto) en la evaluación de una expresión.

## <a name="syntax"></a>Sintaxis

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

Los operadores en este nivel de prioridad son los subíndices de matriz, las llamadas a función, los miembros de estructura y unión, y los operadores postfijos de incremento y decremento.

## <a name="see-also"></a>Vea también

[Operadores de C](../c-language/c-operators.md)