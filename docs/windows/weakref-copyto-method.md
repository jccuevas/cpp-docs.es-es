---
title: "Weakref:: CopyTo (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::CopyTo
dev_langs: C++
helpviewer_keywords: CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca0fe93e89b1a7115e816157fe1842d616850675
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo (Método)
Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<  
   typename U  
>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 Puntero de una interfaz IInspectable. Se genera un error si `U` no se deriva de IInspectable.  
  
 `riid`  
 Id. de interfaz. Se genera un error si `riid` no se deriva de **IWeakReference**.  
  
 `ptr`  
 Puntero indirecto doble para IInspectable o IWeakReference.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Para obtener más información, vea la sección Comentarios.  
  
## <a name="remarks"></a>Comentarios  
 Un valor devuelto de S_OK significa que esta operación se realizó correctamente, pero no indica si la referencia débil se resolvió en una referencia segura. Si se devuelve S_OK, pruebe que ese parámetro `p` es una referencia segura; es decir, el parámetro `p` no es igual a `nullptr`.  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar el código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe `ptr` para `nullptr`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)