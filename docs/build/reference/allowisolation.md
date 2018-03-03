---
title: -ALLOWISOLATION | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0295d73e51e28fbdd953d7d9a3a2ae5131c27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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