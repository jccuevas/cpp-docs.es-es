---
title: CreateActivationFactory (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ab03b15a968c6aba3fa6df8c975fb98e873f8e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214076"
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
Combinación de uno o más valores de enumeración [runtimeclasstype (](runtimeclasstype-enumeration.md) .

*entry*<br/>
Puntero a un [CreatorMap](creatormap-structure.md) que contiene información de inicialización y registro sobre el parámetro *riid*.

*riid*<br/>
Referencia a un identificador de interfaz.

*ppFactory*<br/>
Si esta operación se completa correctamente, un puntero a un generador de activación.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Observaciones

Se emite un error de aserción si el *generador* de parámetros de plantilla no se deriva de la interfaz `IActivationFactory`.

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)
