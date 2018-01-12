---
title: Expresiones de preprocesamiento de archivos MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7bea4f0c4fea2c2d04681674734bc989424c7951
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expressions-in-makefile-preprocessing"></a>Expresiones de preprocesamiento de archivos MAKE
El **! IF** o **! ELSE IF** `constantexpression` consta de las constantes de tipo entero (en notación decimal o de lenguaje C), constantes de cadena o comandos. Utilice paréntesis para agrupar expresiones. Las expresiones usar estilo C con aritmética de enteros largos; los números son en forma de complemento de dos de 32 bits en el intervalo de – 2147483648 a 2147483647.  
  
 Las expresiones pueden usar operadores que actúan sobre valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso de sistema de archivos.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Operadores de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-operators.md)  
  
 [Ejecutar un programa en el preprocesamiento](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>Vea también  
 [Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)