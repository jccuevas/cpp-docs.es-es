---
title: 2.2 compilación condicional | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="22-conditional-compilation"></a>2.2 Compilación condicional
El _**OPENMP** nombre de la macro se define por las implementaciones compatibles con OpenMP como la constante decimal *AAAAMM*, que será el año y mes de la especificación aprobada. Esta macro no debe ser el sujeto de un **#define** o un **#undef** directiva de preprocesamiento.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Si los proveedores definan extensiones de OpenMP, pueden especificar adicionales macros predefinidas.