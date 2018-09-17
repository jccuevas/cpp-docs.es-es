---
title: Las expresiones de preprocesamiento de archivos MAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1070eb01802bd4b39f62ae24519ad6dabca7eb90
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719012"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expresiones de preprocesamiento de archivos MAKE

El **! IF** o **! ELSE IF** `constantexpression` consta de los comandos, las constantes de cadena o constantes de tipo entero (en notación decimal o de lenguaje C). Utilice paréntesis para agrupar expresiones. Las expresiones usan estilo C entero long con signo operaciones aritméticas. los números son en forma de 32 bits de dos complementos en el intervalo de-2147483648 a 2147483647.

Las expresiones pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Operadores de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-operators.md)

[Ejecutar un programa en el preprocesamiento](../build/executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Vea también

[Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)