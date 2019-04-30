---
title: Expresiones de preprocesamiento de archivos MAKE
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 3d668492441eb2fc09be378dbebfe2b18c1b5753
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271312"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expresiones de preprocesamiento de archivos MAKE

El **! IF** o **! ELSE IF** `constantexpression` consta de los comandos, las constantes de cadena o constantes de tipo entero (en notación decimal o de lenguaje C). Utilice paréntesis para agrupar expresiones. Las expresiones usan estilo C entero long con signo operaciones aritméticas. los números son en forma de 32 bits de dos complementos en el intervalo de-2147483648 a 2147483647.

Las expresiones pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Operadores de preprocesamiento de archivos MAKE](makefile-preprocessing-operators.md)

[Ejecutar un programa en el preprocesamiento](executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Vea también

[Preprocesamiento de archivos MAKE](makefile-preprocessing.md)
