---
title: Tipo double
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290738"
---
# <a name="type-double"></a>Tipo double

Los valores de precisión doble con tipo double tienen 8 bytes. El formato es similar al formato float, excepto que tiene un exponente 1023 que supera los 11 bits y una mantisa de 52 bits, más el bit de orden superior implícito. Este formato proporciona un intervalo de aproximadamente 1,7E–308 a 1,7E+308 para el tipo double.

**Específicos de Microsoft**

El tipo double contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa. Su intervalo es +/- 1,7E308 con al menos 15 dígitos de precisión.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)
