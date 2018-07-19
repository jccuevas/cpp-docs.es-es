---
title: setvbuf (Constantes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
dev_langs:
- C++
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d4292ae29602b5890a167a3e2c29e460d65373f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407969"
---
# <a name="setvbuf-constants"></a>setvbuf (Constantes)
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes representan el tipo de búfer para `setvbuf`.  
  
 Los posibles valores se indican mediante las constantes de manifiesto siguientes:  
  
|Constante|Significado|  
|--------------|-------------|  
|`_IOFBF`|Almacenamiento en búfer completo: se usa el búfer especificado en la llamada a `setvbuf` y su tamaño se corresponde con el especificado en la llamada `setvbuf`. Si el puntero de búfer es **NULL**, se usa el búfer del tamaño especificado asignado automáticamente.|  
|`_IOLBF`|Igual a `_IOFBF`.|  
|`_IONBF`|No se usa ningún búfer, con independencia de los argumentos de la llamada a `setvbuf`.|  
  
## <a name="see-also"></a>Vea también  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)