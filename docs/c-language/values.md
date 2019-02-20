---
title: Valores
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: a745b9cc45ed3e58cab4ec7355707d93a0557c04
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150043"
---
# <a name="values"></a>Valores

**ANSI 3.1.2.5** Las representaciones y conjuntos de valores de distintos tipos de números de punto flotante

El tipo **float** contiene 32 bits: 1 para el signo, 8 para el exponente y 23 para la mantisa. El intervalo es +/- 3,4E38 con al menos 7 dígitos de precisión.

El tipo **double** contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa. El intervalo es +/- 1,7E308 con al menos 15 dígitos de precisión.

El tipo **long double** contiene 80 bits: 1 para el signo, 15 para el exponente y 64 para la mantisa. El intervalo es +/- 1,2E4932 con al menos 19 dígitos de precisión. Observe que, con el compilador de Microsoft C, la representación del tipo **long double** es idéntica al tipo **double**.

## <a name="see-also"></a>Vea también

[Matemáticas de punto flotante](../c-language/floating-point-math.md)
