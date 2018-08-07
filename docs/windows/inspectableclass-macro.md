---
title: Inspectableclass (macro) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a02e20f2b87afc312c24683417f808d636c2757f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608961"
---
# <a name="inspectableclass-macro"></a>InspectableClass (Macro)
Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
### <a name="parameters"></a>Parámetros  
 *runtimeClassName*  
 El nombre textual completo de la clase en tiempo de ejecución.  
  
 *trustLevel*  
 Uno de los [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valores enumerados.  
  
## <a name="remarks"></a>Comentarios  
 El **InspectableClass** macro puede utilizarse solo con tipos de Windows en tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClass (clase)](../windows/runtimeclass-class.md)