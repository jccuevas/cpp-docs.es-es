---
title: Compatibilidad del código antiguo con puntos flotantes (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509648"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con puntos flotantes (Visual C++)

Los registros MMX y pila de punto flotante (MM0 MM7/ST0 ST7) se conservan a través de los cambios de contexto.  No hay ninguna convención de llamada explícita para estos registros.  El uso de estos registros está prohibido en el código de modo kernel.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)