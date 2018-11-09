---
title: Valores
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: e0a200bfea8c0a0a06f064b280dad320da25550c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534061"
---
# <a name="values"></a>Valores

**ANSI 3.1.2.5** Las representaciones y conjuntos de valores de distintos tipos de números de punto flotante

El tipo **float** contiene 32 bits: 1 para el signo, 8 para el exponente y 23 para la mantisa. El intervalo es +/- 3,4E38 con al menos 7 dígitos de precisión.

El tipo **double** contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa. El intervalo es +/- 1,7E308 con al menos 15 dígitos de precisión.

El tipo **long double** contiene 80 bits: 1 para el signo, 15 para el exponente y 64 para la mantisa. El intervalo es +/- 1,2E4932 con al menos 19 dígitos de precisión. Observe que, con el compilador de Microsoft C, la representación del tipo **long double** es idéntica al tipo **double**.

## <a name="see-also"></a>Vea también

[Matemáticas de punto flotante](../c-language/floating-point-math.md)