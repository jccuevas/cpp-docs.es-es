---
title: InspectableClass (macro) | Documentos de Microsoft
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
ms.openlocfilehash: 922f7f74771125aed0122c408ef902da2569e5c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873776"
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