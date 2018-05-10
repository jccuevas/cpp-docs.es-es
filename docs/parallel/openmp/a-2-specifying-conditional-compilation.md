---
title: A.2 especificando la compilación condicional | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d54245a2df2f38bed2674a3bb3923f8212d35459
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a2---specifying-conditional-compilation"></a>A.2 Especificar una compilación condicional
Los siguientes ejemplos ilustran el uso de la compilación condicional mediante la macro de OpenMP `_OPENMP` ([sección 2.2](../../parallel/openmp/2-2-conditional-compilation.md) en página 8). Con la compilación de OpenMP, el `_OPENMP` macro queda definida.  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 El operador de preprocesador definido permite más de una macro se va a probar en una única directiva.  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```