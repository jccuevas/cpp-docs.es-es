---
title: Varargs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8305eaddf87a2e67b797bedff1944dbcbbbdbd41
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713653"
---
# <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, los argumentos de puntos suspensivos), esencialmente el parámetro normal pasando aplica incluyendo los argumentos de la quinto y posteriores. Nuevo es responsabilidad del destinatario para volcar los argumentos ceder su dirección. Para valores de punto flotante, el entero y el registro de punto flotante contendrá el valor de punto flotante en caso de que el destinatario espere el valor de los registros enteros.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)