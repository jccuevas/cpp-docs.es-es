---
title: Asiid (método) | Microsoft Docs
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
ms.openlocfilehash: 60d2900876d7a9fbee7a193d0575bf3afdf4335b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012185"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID (Método)
Establece el texto especificado `ComPtr` parámetro de puntero para representar el identificador de interfaz especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *riid*  
 Id. de interfaz.  
  
 *ptr*  
 Cuando finalice esta operación, un objeto que representa el parámetro *riid*.  
  
## <a name="return-value"></a>Valor devuelto  
  
-   S_OK si esta operación se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación, y *ptr* está establecido en **nullptr**.  
  
-   S_OK si esta operación se realiza correctamente, pero actual **WeakRef** objeto ya se ha liberado. Parámetro *ptr* está establecido en **nullptr**.  
  
-   S_OK si esta operación se realiza correctamente, pero actual **WeakRef** objeto no se deriva de parámetro *riid*. Parámetro *ptr* está establecido en **nullptr**. (Para más información, vea la sección Comentarios.)  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error si parámetro *riid* no se deriva `IInspectable`. Este error sustituye el valor devuelto.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla (no se muestra aquí, pero se declara en el archivo de encabezado) es una especialización de aplicación auxiliar interna, que admite características del lenguaje C++, como la palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .  
  
 A partir del SDK de Windows 10, este método no establece la **WeakRef** instancia a **nullptr** si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la **WeakRef** para **nullptr**. En su lugar, compruebe *ptr* para **nullptr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)