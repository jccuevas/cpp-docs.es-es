---
title: GetActivationFactory (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1a4bf31ff44c74362e21e8888630273fcc049e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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