---
title: "Weakref:: Asiid (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fdefa73ac14e807c5e4100fd81e1d931f4bf6e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID (Método)
Establece el parámetro de puntero ComPtr especificado para representar el id. de interfaz especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Id. de interfaz.  
  
 `ptr`  
 Cuando se completa esta operación, un objeto que representa el parámetro `riid`.  
  
## <a name="return-value"></a>Valor devuelto  
  
-   S_OK si esta operación es correcta; de lo contrario, un HRESULT que indica el motivo del error de la operación y `ptr` se establece en `nullptr`.  
  
-   S_OK si esta operación es correcta, pero el objeto WeakRef actual ya se ha liberado. El parámetro `ptr` se establece en `nullptr`.  
  
-   S_OK si esta operación se realiza correctamente, pero el objeto WeakRef actual no se deriva del parámetro `riid`. El parámetro `ptr` se establece en `nullptr`. (Para más información, vea la sección Comentarios.)  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error si el parámetro `riid` no se deriva de IInspectable. Este error sustituye el valor devuelto.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla (no se muestra aquí, pero se declara en el archivo de encabezado) es una especialización de aplicación auxiliar interna, que admite características del lenguaje C++, como la palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe `ptr` para `nullptr`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)