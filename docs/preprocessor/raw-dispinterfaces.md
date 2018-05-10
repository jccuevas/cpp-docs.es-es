---
title: raw_dispinterfaces | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f2a0d91d0f0dd3d23886ade75072526e6c895f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Específicos de C++**  
  
 Indica al compilador que genere funciones de contenedor de bajo nivel de métodos y propiedades que llaman a dispinterface **IDispatch:: Invoke** y devolver la `HRESULT` código de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica este atributo, solo se generan los contenedores de alto nivel, que inician excepciones de C++ en caso de error.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)