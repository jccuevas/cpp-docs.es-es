---
title: Método Simpleclassfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aa0d48ba96c550ff6ee1248dccd0b4c8e3021212
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020309"
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance (Método)

Crea una instancia de la interfaz especificada.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

### <a name="parameters"></a>Parámetros
*pUnkOuter*  
Debe ser **nullptr**; en caso contrario, el valor devuelto es CLASS_E_NOAGGREGATION.

SimpleClassFactory no admite la agregación. Si se admite la agregación y el objeto se crea formaba parte de un agregado, *pUnkOuter* sería un puntero al control `IUnknown` interfaz del agregado.

*riid*  
Identificador del objeto para crear la interfaz.

*ppvObject*  
Cuando finalice esta operación, puntero a una instancia del objeto especificado por el *riid* parámetro.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Si `__WRL_STRICT__` está definido, se genera un error de aserción si no se deriva de la clase base especificada en el parámetro de plantilla de clase [RuntimeClass](../windows/runtimeclass-class.md), o no está configurado con el ClassicCom o WinRtClassicComMix [ RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
 [SimpleClassFactory (clase)](../windows/simpleclassfactory-class.md)