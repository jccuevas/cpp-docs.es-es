---
title: Conversiones de asignación
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: f118c4a7fee493793b1410cb26f6a0af571c5fcc
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998694"
---
# <a name="assignment-conversions"></a>Conversiones de asignación

En las operaciones de asignación, el tipo de valor que se va a asignar se convierte al tipo de la variable que recibe la asignación. C permite realizar conversiones por asignación entre tipos enteros y de punto flotante, aunque se pierda información en la conversión. El método de conversión utilizado depende de los tipos usados en la asignación, como se describe en [Conversiones aritméticas usuales](../c-language/usual-arithmetic-conversions.md) y en las siguientes secciones:

- [Conversiones de tipos enteros con signo](../c-language/conversions-from-signed-integral-types.md)

- [Conversiones de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md)

- [Conversiones de tipos de punto flotante](../c-language/conversions-from-floating-point-types.md)

- [Conversiones entre tipos de puntero](../c-language/conversions-to-and-from-pointer-types.md)

- [Conversiones de otros tipos](../c-language/conversions-from-other-types.md)

Los calificadores de tipo no afectan a la capacidad de realizar una conversión, pero no se puede usar un valor L **const** en el lado izquierdo de la asignación.

## <a name="see-also"></a>Vea también

[Conversiones de tipos](../c-language/type-conversions-c.md)
