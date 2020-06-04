---
title: CreateClassFactory (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214063"
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
Combinación de uno o más valores de enumeración [runtimeclasstype (](runtimeclasstype-enumeration.md) .

*entry*<br/>
Puntero a un [CreatorMap](creatormap-structure.md) que contiene información de inicialización y registro sobre el parámetro *riid*.

*riid*<br/>
Referencia a un identificador de interfaz.

*ppFactory*<br/>
Si esta operación se completa correctamente, un puntero a un generador de clases.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Observaciones

Se emite un error de aserción si el *generador* de parámetros de plantilla no se deriva de la interfaz `IClassFactory`.

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)
