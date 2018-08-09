---
title: Método Weakref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88a092255655aaea0e06e8f69b520789f441d379
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016293"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo (Método)
Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *U*  
 Puntero un `IInspectable` interfaz. Se genera un error si *U* no se deriva `IInspectable`.  
  
 *riid*  
 Id. de interfaz. Se genera un error si *riid* no se deriva `IWeakReference`.  
  
 *ptr*  
 Un puntero indirecto doble a `IInspectable` o `IWeakReference`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Para obtener más información, vea **Comentarios**.  
  
## <a name="remarks"></a>Comentarios  
 Un valor devuelto de S_OK significa que esta operación se realizó correctamente, pero no indica si la referencia débil se resolvió en una referencia segura. Si se devuelve S_OK, pruebe que ese parámetro *p* una fuerte referencia; es decir, el parámetro *p* no es igual a **nullptr**.  
  
 A partir del SDK de Windows 10, este método no establece la **WeakRef** instancia a **nullptr** si no se pudo obtener la referencia débil, por lo que debería evitar código que comprueba la WeakRef para de comprobación de errores **nullptr**. En su lugar, compruebe *ptr* para **nullptr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)