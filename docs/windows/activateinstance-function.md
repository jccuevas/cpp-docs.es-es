---
title: "ActivateInstance (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 051eb51a4461d1b3f9ab180507022cdfa955f0ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activateinstance-function"></a>ActivateInstance (función)
Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un tipo a activar.  
  
 `activatableClassId`  
 El nombre del identificador de clase que define el parámetro `T`.  
  
 `instance`  
 Cuando se completa esta operación, una referencia a una instancia de `T`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** Windows::Foundation  
  
## <a name="see-also"></a>Vea también  
 [Windows::Foundation (espacio de nombres)](../windows/windows-foundation-namespace.md)