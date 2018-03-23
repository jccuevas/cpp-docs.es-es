---
title: 'Runtimeclassbaset:: Asiid (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17d67ee58e9ecc3b0ef463d6af132fec3a1c0a2f
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un tipo que implementa el identificador de interfaz especificado por el parámetro `riid`.  
  
 `implements`  
 Una variable del tipo especificado por el parámetro de plantilla `T`.  
  
 `riid`  
 El identificador de interfaz para recuperar.  
  
 `ppvObject`  
 Si esta operación se realiza correctamente, un puntero a un-puntero a la interfaz especificada por el parámetro `riid`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Recupera un puntero al identificador de interfaz especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)