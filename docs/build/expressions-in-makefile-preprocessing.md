---
title: Expresiones de preprocesamiento de archivos MAKE | Documentos de Microsoft
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
ms.openlocfilehash: 04a53e5e6fe45c2c846cae3fb9e973fe1c712107
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="expressions-in-makefile-preprocessing"></a>Expresiones de preprocesamiento de archivos MAKE
El **! IF** o **! ELSE IF** `constantexpression` consta de las constantes de tipo entero (en notación decimal o de lenguaje C), constantes de cadena o comandos. Utilice paréntesis para agrupar expresiones. Las expresiones usar estilo C con aritmética de enteros largos; los números son en forma de complemento de dos de 32 bits en el intervalo de – 2147483648 a 2147483647.  
  
 Las expresiones pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso de sistema de archivos.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Operadores de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-operators.md)  
  
 [Ejecutar un programa en el preprocesamiento](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>Vea también  
 [Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)