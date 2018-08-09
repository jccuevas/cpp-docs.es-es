---
title: CreateClassFactory (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57759e7191ecbe08e6d94dcec798f6d3203c13de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645144"
---
# <a name="createclassfactory-function"></a>CreateClassFactory (función)
Crea un generador que produce instancias de la clase especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *flags*  
 Una combinación de uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valores de enumeración.  
  
 *entry*  
 Puntero a un [CreatorMap](../windows/creatormap-structure.md) que contiene información de inicialización y el registro sobre el parámetro *riid*.  
  
 *riid*  
 Referencia a un identificador de interfaz.  
  
 *ppFactory*  
 Si esta operación completa correctamente, un puntero a un generador de clases.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error de aserción si el parámetro de plantilla *Factory* no se deriva de la interfaz `IClassFactory`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)