---
title: CreateActivationFactory (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ca3469128cf3d412138d5d39a1587cbc20150699
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040611"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory (función)

Crea un generador que produce instancias de la clase especificada que puede activar Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Una combinación de uno o varios [RuntimeClassType](runtimeclasstype-enumeration.md) valores de enumeración.

*entry*<br/>
Puntero a un [CreatorMap](creatormap-structure.md) que contiene información de inicialización y el registro sobre el parámetro *riid*.

*riid*<br/>
Referencia a un identificador de interfaz.

*ppFactory*<br/>
Si esta operación completa correctamente, un puntero a un generador de activación.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Se genera un error de aserción si el parámetro de plantilla *Factory* no se deriva de la interfaz `IActivationFactory`.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)