---
title: no_registry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105c2b0ee4d2648a1cc43d0baca9f30146184e78
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541658"
---
# <a name="noregistry"></a>no_registry
**no_registry** indica al compilador que no busque en el registro bibliotecas de tipos importadas con `#import`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#import filename no_registry  
```  
  
### <a name="parameters"></a>Parámetros  
*filename*  
Una biblioteca de tipos.  
  
## <a name="remarks"></a>Comentarios  
 
Si no se encuentra una biblioteca de tipos que se hace referencia en los directorios de inclusión, se producirá un error en la compilación incluso si la biblioteca de tipos está en el registro.  **no_registry** se propaga a otras bibliotecas de tipos importadas implícitamente con `auto_search`.  
  
El compilador nunca buscará en el registro bibliotecas de tipos especificadas por nombre de archivo y que se hayan pasado directamente a `#import`.  
  
Cuando `auto_search` se especifica, el adicionales `#import`s se generará con el **no_registry** configuración de la inicial `#import` (si inicial `#import` directiva fue **no_registry** , un `auto_search`-genera `#import` también es **no_registry**.)  
  
**no_registry** es útil si desea importar bibliotecas de tipo de referencia sin el riesgo de que el compilador encuentre una versión anterior del archivo en el registro. **no_registry** también es útil si la biblioteca de tipos no está registrada.  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)