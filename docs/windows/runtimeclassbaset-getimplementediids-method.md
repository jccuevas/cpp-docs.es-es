---
title: Método Runtimeclassbaset | Microsoft Docs
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
ms.openlocfilehash: 2a5c63a3b2dbbac934162f74abb8e742cc4418a7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018996"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 El tipo de la *implementa* parámetro.  
  
 *Implementa*  
 Puntero al tipo especificado por el parámetro *T*.  
  
 *iidCount*  
 El número máximo de identificadores de interfaz para recuperar.  
  
 *IID*  
 Si esta operación completa correctamente, una matriz de la interfaz implementadas por el tipo de identificadores *T*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Recupera una matriz de identificadores que se implementan mediante un tipo especificado de interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)