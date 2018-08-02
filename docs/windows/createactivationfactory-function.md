---
title: CreateActivationFactory (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fd2f65bb86cdd77d4e285cee5603416fa629f940
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466353"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory (función)
Crea un generador que produce instancias de la clase especificada que puede activar Windows Runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<typename Factory>  
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(  
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,   
      REFIID riid,   
     _Outptr_ IUnknown **ppFactory) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *flags*  
 Una combinación de uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valores de enumeración.  
  
 *entry*  
 Puntero a un [CreatorMap](../windows/creatormap-structure.md) que contiene información de inicialización y el registro sobre el parámetro *riid*.  
  
 *riid*  
 Referencia a un identificador de interfaz.  
  
 *ppFactory*  
 Si esta operación completa correctamente, un puntero a un generador de activación.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Se genera un error de aserción si el parámetro de plantilla *Factory* no se deriva de la interfaz `IActivationFactory`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)