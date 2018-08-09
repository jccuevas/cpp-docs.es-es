---
title: Método Runtimeclass | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91d0a082a422657f6716e16c8b53ab33e0313d82
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020140"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids (Método)
Obtiene una matriz que puede contener la interfaz implementadas por la actual de identificadores **RuntimeClass** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Parámetros  
 *iidCount*  
 Cuando finalice esta operación, el número total de elementos de matriz *IID*.  
  
 *IID*  
 Cuando se completa esta operación, un puntero a una matriz de identificadores de interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClass (clase)](../windows/runtimeclass-class.md)