---
title: CompareStringOrdinal (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3abf87340671d1ac4851b055a57896e340d0c20
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera HSTRING para comparar.  
  
 `rhs`  
 El segundo HSTRING para comparar.  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Condición|  
|-----------|---------------|  
|-1|`lhs` es menor que `rhs`.|  
|0|`lhs` es igual que `rhs`.|  
|1|`lhs` es mayor que `rhs`.|  
  
## <a name="remarks"></a>Comentarios  
 Compara dos objetos HSTRING especificados y devuelve un entero que indica su posición relativa en un criterio de ordenación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)