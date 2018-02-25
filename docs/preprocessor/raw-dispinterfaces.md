---
title: raw_dispinterfaces | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9c20cc7cab6c85f203bc83523229f50749332f3d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C++ Specific**  
  
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