---
title: 'Runtimeclassbaset:: Getimplementediids (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ea6ff871ef0ce886b393c948fc45accf3d8e245
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892239"
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
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)