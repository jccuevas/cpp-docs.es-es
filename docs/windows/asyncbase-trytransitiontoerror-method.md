---
title: Trytransitiontoerror (método) | Microsoft Docs
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
ms.openlocfilehash: fc677304ae7ab61e6726366869e85f731cd92484
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463212"
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
 *Error*  
 Un HRESULT de error.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si el estado de error interno se ha cambiado; en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Esta operación modifica el estado de error únicamente si el estado de error ya está establecido en S_OK. Esta operación no tiene ningún efecto si el estado de error ya es error, cancelado, completado o cerrado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)