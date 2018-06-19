---
title: -ALLOWISOLATION | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cb92a7f31d48dad4a7fb608703c71ccc661e176
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368979"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Especifica el comportamiento de la búsqueda de manifiesto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ ALLOWISOLATION** hace que el sistema operativo realice búsquedas y cargas de manifiestos.  
  
 **/ ALLOWISOLATION** es el valor predeterminado.  
  
 **/ALLOWISOLATION:no** indica que los archivos ejecutables se cargan como si no hubiera ningún manifiesto y hace [referencia de EDITBIN](../../build/reference/editbin-reference.md) para establecer el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` de bits en el encabezado opcional `DllCharacteristics` campo.  
  
 Cuando se deshabilita el aislamiento para un ejecutable, el cargador de Windows no busca ningún manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tiene un contexto de activación predeterminado, incluso si hay un manifiesto en el propio ejecutable o si hay un manifiesto con el nombre *nombre de archivo ejecutable*. exe.manifest.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [/ /ALLOWISOLATION (manifestar)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Referencia de archivos del manifiesto](http://msdn.microsoft.com/library/aa375632.aspx)