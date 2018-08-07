---
title: GetActivationFactory (función) | Microsoft Docs
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
ms.openlocfilehash: 2cbb5be3603f79a7df1cb330ca06775357666854
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570316"
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
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Un parámetro de plantilla que especifica el tipo de la factoría de activación.  
  
 *activatableClassId*  
 El nombre de la clase que puede producir el generador de activación.  
  
 *Factory*  
 Cuando finalice esta operación, una referencia a la factoría de activación para el tipo *T*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo del error de esta operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** Windows::Foundation  
  
## <a name="see-also"></a>Vea también  
 [Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)