---
title: 'Implementshelper:: Cancastto (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 9ae6fa17-d0b1-4e31-9ae5-da6ae4026e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6de971f2de2421a2d7987dab30ba73fa2d225b15
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876558"
---
# <a name="implementshelpercancastto-method"></a>ImplementsHelper::CanCastTo (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
HRESULT CanCastTo(  
   _In_ const IID &iid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Referencia a un identificador de interfaz.  
  
 `ppv`  
 Si esta operación se realiza correctamente, un puntero a la interfaz especificada por `riid` o `iid`.  
  
 `iid`  
 Referencia a un identificador de interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Obtiene un puntero al identificador de interfaz especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ImplementsHelper (estructura)](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)