---
title: InspectableClass (macro) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ac1f84c76bb61d24ee25e8ca431e13620f6f85a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="inspectableclass-macro"></a>InspectableClass (Macro)
Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtimeClassName`  
 El nombre de texto completo de la clase en tiempo de ejecución.  
  
 `trustLevel`  
 Uno de los [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valores enumerados.  
  
## <a name="remarks"></a>Comentarios  
 El `InspectableClass` macro puede utilizarse solo con los tipos en tiempo de ejecución de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClass (clase)](../windows/runtimeclass-class.md)