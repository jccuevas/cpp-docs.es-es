---
title: Cancastto (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a73aac6fb36270f0cd04615d9e530b29841850f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010927"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo (Método)
Obtiene un puntero a la interfaz especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *riid*  
 Una referencia a un identificador de interfaz.  
  
 *PPV*  
 Si es correcto, un puntero a la interfaz especificada por *riid*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un HRESULT que indica el error, como E_NOINTERFACE.  
  
## <a name="remarks"></a>Comentarios  
 Se trata de una función auxiliar interna que realiza una operación de QueryInterface.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Implements (estructura)](../windows/implements-structure.md)