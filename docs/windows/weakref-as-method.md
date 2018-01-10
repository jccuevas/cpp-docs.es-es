---
title: "Weakref:: As (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::As
dev_langs: C++
helpviewer_keywords: As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e18ebeb8c50a4bae35c53fc82f059642a88cef07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefas-method"></a>WeakRef::As (Método)
Establece el parámetro de puntero ComPtr especificado para representar la interfaz especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 Id. de interfaz.  
  
 `ptr`  
 Cuando se completa esta operación, un objeto que representa el parámetro `U`.  
  
## <a name="return-value"></a>Valor devuelto  
  
-   S_OK si esta operación es correcta; de lo contrario, un HRESULT que indica el motivo del error de la operación y `ptr` se establece en `nullptr`.  
  
-   S_OK si esta operación es correcta, pero el objeto WeakRef actual ya se ha liberado. El parámetro `ptr` se establece en `nullptr`.  
  
-   S_OK si esta operación se realiza correctamente, pero el objeto WeakRef actual no se deriva del parámetro `U`. El parámetro `ptr` se establece en `nullptr`.  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error si el parámetro `U` es IWeakReference, o no se deriva de IInspectable.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización de aplicación auxiliar interna, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe `ptr` para `nullptr`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)