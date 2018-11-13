---
title: Conversión de enteros a valores de punto flotante
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: d19544e3b4f0bf3978d296c996c204fc9d60fa0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667355"
---
# <a name="casting-integers-to-floating-point-values"></a>Conversión de enteros a valores de punto flotante

**ANSI 3.2.1.3** La dirección de truncamiento cuando un número entero se convierte en un número de punto flotante que no puede representar exactamente el valor original

Cuando un número entero se convierte en un valor de punto flotante que no puede representar exactamente el valor, el valor se redondea (arriba o abajo) al valor apropiado más próximo.

Por ejemplo, la conversión de **unsigned long** (con 32 bits de precisión) a **float** (cuya mantisa tiene 23 bits de precisión) redondea el número al múltiplo más próximo de 256. Los valores **long** 4.294.966.913 a 4.294.967.167 se redondean todos al valor **float** 4.294.967.040.

## <a name="see-also"></a>Vea también

[Matemáticas de punto flotante](../c-language/floating-point-math.md)