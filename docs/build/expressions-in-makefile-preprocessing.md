---
title: Expresiones de preprocesamiento de archivos MAKE
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 8d7b8cd489eabf239cbc993181142ca84431cd82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594875"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expresiones de preprocesamiento de archivos MAKE

El **! IF** o **! ELSE IF** `constantexpression` consta de los comandos, las constantes de cadena o constantes de tipo entero (en notación decimal o de lenguaje C). Utilice paréntesis para agrupar expresiones. Las expresiones usan estilo C entero long con signo operaciones aritméticas. los números son en forma de 32 bits de dos complementos en el intervalo de-2147483648 a 2147483647.

Las expresiones pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Operadores de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-operators.md)

[Ejecutar un programa en el preprocesamiento](../build/executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Vea también

[Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)