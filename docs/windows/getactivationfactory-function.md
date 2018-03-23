---
title: GetActivationFactory (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd269b8c2e1c671944305d385064d60e8bf9b8a1
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="getactivationfactory-function"></a>GetActivationFactory (función)
Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un parámetro de plantilla que especifica el tipo de la fábrica de activación.  
  
 `activatableClassId`  
 El nombre de la clase que puede producir el generador de activación.  
  
 `factory`  
 Cuando se completa esta operación, una referencia a la fábrica de activación para su tipo `T`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo del error de esta operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** Windows::Foundation  
  
## <a name="see-also"></a>Vea también  
 [Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)