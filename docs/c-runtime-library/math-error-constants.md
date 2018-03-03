---
title: "Constantes de error matemático | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs:
- C++
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76313854bc9bb7c9a624836c47d0178978f8befd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-constants"></a>Constantes de error matemático
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las rutinas matemáticas de la biblioteca en tiempo de ejecución pueden generar constantes de error matemático.  
  
 Estos errores, que se describen como sigue, corresponden a los tipos de excepción definidos en MATH.H y los devuelve la función `_matherr` cuando se produce un error matemático.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_DOMAIN`|El argumento de la función está fuera del dominio de la función.|  
|`_OVERFLOW`|El resultado es demasiado grande para representarlo en el tipo de valor devuelto de la función.|  
|`_PLOSS`|Se ha producido una pérdida parcial de significación.|  
|`_SING`|Singularidad del argumento: el argumento de la función tiene un valor no válido. (Por ejemplo, el valor 0 se pasa a la función que requiere un valor distinto de cero).|  
|`_TLOSS`|Se ha producido una pérdida total de significación.|  
|`_UNDERFLOW`|El resultado es demasiado pequeño para representarlo.|  
  
## <a name="see-also"></a>Vea también  
 [_matherr](../c-runtime-library/reference/matherr.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)