---
title: Platform::IBoxArray (Interfaz)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: a35a8b7d9f23bcb624755353e27e52de4b873c5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497048"
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

### <a name="remarks"></a>Comentarios

`IBoxArray` es C++ / c++ / nombre CX para `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Miembros

La interfaz `IBoxArray` hereda de la interfaz `IValueType` . `IBoxArray` también tiene estos miembros:

|Método|Descripción|
|------------|-----------------|
|[Valor](#value)|Devuelve la matriz a la que se le ha aplicado la conversión unboxing y que se almacenó previamente en esta instancia de `IBoxArray` .|

## <a name="value"></a> Propiedad Iboxarray

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

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo, vea [Boxing](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Vea también

[Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)