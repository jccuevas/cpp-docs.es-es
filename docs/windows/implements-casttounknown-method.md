---
title: Casttounknown (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: efaf7b51da1e4a4e744133884b92ac78db3b3f66
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017775"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown (Método)
Obtiene un puntero subyacente `IUnknown` interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Esta operación siempre se realiza correctamente y devuelve el `IUnknown` puntero.  
  
## <a name="remarks"></a>Comentarios  
 Función auxiliar interno.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Implements (estructura)](../windows/implements-structure.md)