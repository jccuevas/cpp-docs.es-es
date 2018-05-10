---
title: 'Weakref:: Asiid (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69108681b181d0b2fce20f9e30a009b6b93c2180
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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