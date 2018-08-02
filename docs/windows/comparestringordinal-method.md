---
title: CompareStringOrdinal (método) | Microsoft Docs
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
ms.openlocfilehash: 58e808510868e375672ee5de0b27c4bed3c568e0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464056"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *LHS*  
 La primera HSTRING para comparar.  
  
 *RHS*  
 El segundo HSTRING para comparar.  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Condición|  
|-----------|---------------|  
|-1|*LHS* es menor que *rhs*.|  
|0|*LHS* es igual a *rhs*.|  
|1|*LHS* es mayor que *rhs*.|  
  
## <a name="remarks"></a>Comentarios  
 Compara dos objetos HSTRING especificados y devuelve un entero que indica su posición relativa en un criterio de ordenación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)