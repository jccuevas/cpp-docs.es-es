---
title: 'Runtimeclassbaset:: Getimplementediids (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 478be22e54732cccddbc212cdb192c2847a1a235
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo del parámetro `implements`.  
  
 `implements`  
 Puntero al tipo especificado por el parámetro `T`.  
  
 `iidCount`  
 El número máximo de identificadores de interfaz se van a recuperar.  
  
 `iids`  
 Si esta operación completa correctamente, una matriz de los identificadores implementadas por el tipo de interfaz `T`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Recupera una matriz de identificadores que se implementan mediante un tipo especificado de interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)