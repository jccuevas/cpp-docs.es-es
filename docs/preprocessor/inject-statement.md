---
title: inject_statement | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 115f5b3d7012ae3e9073d81e0c1005dcb513e045
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="injectstatement"></a>inject_statement
**Específicos de C++**  
  
 Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `source_text`  
 Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.  
  
## <a name="remarks"></a>Comentarios  
 El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)