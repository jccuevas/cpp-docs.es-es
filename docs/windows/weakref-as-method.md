---
title: Método Weakref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 938c7c796bf88d4ea1e49f1f59d274b5017aa7de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649307"
---
# <a name="weakrefas-method"></a>WeakRef::As (Método)
Establece el texto especificado `ComPtr` parámetro de puntero para representar la interfaz especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *U*  
 Id. de interfaz.  
  
 *ptr*  
 Cuando finalice esta operación, un objeto que representa el parámetro *U*.  
  
## <a name="return-value"></a>Valor devuelto  
  
-   S_OK si esta operación se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación, y *ptr* está establecido en **nullptr**.  
  
-   S_OK si esta operación se realiza correctamente, pero actual **WeakRef** objeto ya se ha liberado. Parámetro *ptr* está establecido en **nullptr**.  
  
-   S_OK si esta operación se realiza correctamente, pero actual **WeakRef** objeto no se deriva de parámetro *U*. Parámetro *ptr* está establecido en **nullptr**.  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error si parámetro *U* es `IWeakReference`, o no se deriva `IInspectable`.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización de aplicación auxiliar interna, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .  
  
 A partir del SDK de Windows 10, este método no establece la **WeakRef** instancia a **nullptr** si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la WeakRef para **nullptr**. En su lugar, compruebe *ptr* para **nullptr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)