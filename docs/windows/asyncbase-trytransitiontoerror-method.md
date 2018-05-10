---
title: 'Asyncbase:: Trytransitiontoerror (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97fcade98e82a289c172c7651f62f3de0394fe16
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError (Método)
Indica si el código de error especificado puede modificar el estado de error interno.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `error`  
 Un valor HRESULT de error.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si se cambió el estado de error interno; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Esta operación modifica el estado de error sólo si el estado de error ya está establecido en S_OK. Esta operación no tiene ningún efecto si el estado de error ya es error, cancelado, completado o cerrado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)