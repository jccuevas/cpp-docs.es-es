---
title: Tipo double
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 42f8ed943fd9d034d5cae8cb057e094363b27d8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532267"
---
# <a name="type-double"></a>Tipo double

Los valores de precisión doble con tipo double tienen 8 bytes. El formato es similar al formato float, excepto que tiene un exponente 1023 que supera los 11 bits y una mantisa de 52 bits, más el bit de orden superior implícito. Este formato proporciona un intervalo de aproximadamente 1,7E–308 a 1,7E+308 para el tipo double.

**Específicos de Microsoft**

El tipo double contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa. Su intervalo es +/- 1,7E308 con al menos 15 dígitos de precisión.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)