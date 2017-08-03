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
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 8dd5321d924d02ef7669166a210b193329abc13a
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

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
