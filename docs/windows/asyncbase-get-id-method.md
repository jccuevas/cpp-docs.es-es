---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea5efa31a3ebff3c86800a023e3525589952c2fc
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464719"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id (Método)
Recupera el identificador de la operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   get_Id  
)(unsigned int *id) override;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *identificador*  
 La ubicación donde se almacenará el identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Comentarios  
 Este método implementa `IAsyncInfo::get_Id`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)