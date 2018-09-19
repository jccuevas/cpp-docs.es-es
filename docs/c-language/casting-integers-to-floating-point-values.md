---
title: Conversión de enteros a valores de punto flotante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a81b72a7dfedbc1d6033d53bde63be22943abb08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055226"
---
# <a name="casting-integers-to-floating-point-values"></a>Conversión de enteros a valores de punto flotante

**ANSI 3.2.1.3** La dirección de truncamiento cuando un número entero se convierte en un número de punto flotante que no puede representar exactamente el valor original

Cuando un número entero se convierte en un valor de punto flotante que no puede representar exactamente el valor, el valor se redondea (arriba o abajo) al valor apropiado más próximo.

Por ejemplo, la conversión de **unsigned long** (con 32 bits de precisión) a **float** (cuya mantisa tiene 23 bits de precisión) redondea el número al múltiplo más próximo de 256. Los valores **long** 4.294.966.913 a 4.294.967.167 se redondean todos al valor **float** 4.294.967.040.

## <a name="see-also"></a>Vea también

[Matemáticas de punto flotante](../c-language/floating-point-math.md)