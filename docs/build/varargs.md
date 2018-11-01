---
title: Varargs
ms.date: 11/04/2016
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
ms.openlocfilehash: 42647949fbc69f7c4f1140352d0be0bb6bd9018c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488002"
---
# <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, los argumentos de puntos suspensivos), esencialmente el parámetro normal pasando aplica incluyendo los argumentos de la quinto y posteriores. Nuevo es responsabilidad del destinatario para volcar los argumentos ceder su dirección. Para valores de punto flotante, el entero y el registro de punto flotante contendrá el valor de punto flotante en caso de que el destinatario espere el valor de los registros enteros.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)