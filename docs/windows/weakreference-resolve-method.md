---
title: "WeakReference:: Resolve (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4da4689ffd8fa0a633b3f481b0292d060e57345
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Id. de interfaz.  
  
 `ppvObject`  
 Cuando se completa esta operación, una copia de la referencia segura actual si el recuento de referencia segura es distinto de cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
-   S_OK si esta operación se realiza correctamente y el recuento de referencia segura es cero. El parámetro `ppvObject` debe establecerse en `nullptr`.  
  
-   S_OK si esta operación se realiza correctamente y el recuento de referencia segura es distinto de cero. El `ppvObject` parámetro está establecido en la referencia segura.  
  
-   En caso contrario, un valor HRESULT que indica la razón por la operación falló.  
  
## <a name="remarks"></a>Comentarios  
 Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [WeakReference Class1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)