---
title: Platform::IBoxArray (Interfaz)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444160"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray (Interfaz)

`IBoxArray` es el contenedor de matrices de los tipos de valor que se pasan a través de la interfaz binaria de aplicación (ABI) o se almacenan en colecciones de elementos `Platform::Object^` como los de los controles XAML.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del valor al que se ha aplicado la conversión boxing en cada elemento de la matriz.

### <a name="remarks"></a>Observaciones

`IBoxArray` es el C++nombre de/cx para `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Members

La interfaz `IBoxArray` hereda de la interfaz `IValueType` . `IBoxArray` también tiene estos miembros:

|Método|Descripción|
|------------|-----------------|
|[Valor](#value)|Devuelve la matriz a la que se le ha aplicado la conversión unboxing y que se almacenó previamente en esta instancia de `IBoxArray` .|

## <a name="value"></a>IBoxArray:: Value (propiedad)

Devuelve el valor que se almacenó originalmente en este objeto.

### <a name="syntax"></a>Sintaxis

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del valor al que se le ha aplicado la conversión boxing.

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Devuelve el valor que se almacenó originalmente en este objeto.

### <a name="remarks"></a>Observaciones

Para obtener un ejemplo, vea [conversión boxing](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Consulte también

[Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
