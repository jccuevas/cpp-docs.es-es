---
title: Get_errorcode (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fab750ce655add3ccdac9d955e1e3a36e46f8cc5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465134"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode (Método)
Recupera el código de error para la operación asincrónica actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *código de error*  
 La ubicación donde se almacena el código de error actual.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL si la operación asincrónica actual está cerrada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)