---
title: Conversiones de asignación
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: 6caed3d7a8079bc6b02e9ad17859cd4062cbee7f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152721"
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
