---
title: CreateClassFactory (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 323fce053707d6d00d1e17b641613d15607ab6f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398659"
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

*flags*<br/>
Una combinación de uno o varios [RuntimeClassType](runtimeclasstype-enumeration.md) valores de enumeración.

*entry*<br/>
Puntero a un [CreatorMap](creatormap-structure.md) que contiene información de inicialización y el registro sobre el parámetro *riid*.

*riid*<br/>
Referencia a un identificador de interfaz.

*ppFactory*<br/>
Si esta operación completa correctamente, un puntero a un generador de clases.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Se genera un error de aserción si el parámetro de plantilla *Factory* no se deriva de la interfaz `IClassFactory`.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)