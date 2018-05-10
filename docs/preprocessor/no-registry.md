---
title: no_registry | Documentos de Microsoft
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
ms.openlocfilehash: 416663592f4362c110637fb4d4b4b418d9776cde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="noregistry"></a>no_registry
`no_registry` indica al compilador que no busque en el registro bibliotecas de tipos importadas con `#import`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#import filename no_registry  
```  
  
#### <a name="parameters"></a>Parámetros  
 *filename*  
 Una biblioteca de tipos.  
  
## <a name="remarks"></a>Comentarios  
 Si una biblioteca de tipos que se hace referencia no se encuentra en los directorios de inclusión, se producirá un error en la compilación aun cuando la biblioteca de tipos está en el registro.  `no_registry` se propaga a otras bibliotecas de tipos que se importan de forma implícita con `auto_search`.  
  
 El compilador nunca buscará en el registro bibliotecas de tipos especificadas por nombre de archivo y que se hayan pasado directamente a `#import`.  
  
 Cuando se especifica `auto_search`, los `#import` adicionales aparecerán con la configuración `no_registry` del `#import` inicial (si la directiva `#import` inicial era `no_registry`, un `auto_search` generado mediante `#import` también es `no_registry`.)  
  
 `no_registry` es útil si van a importar las bibliotecas de tipos de referencia cruzada sin el riesgo de que el compilador detecta una versión anterior del archivo en el registro.  `no_registry` También es útil si la biblioteca de tipos no está registrada.  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)