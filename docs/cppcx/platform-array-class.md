---
title: Platform::Array (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 7d9fca4de954b5ba9c7cbcb3bdfce0fe3263dbd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445800"
---
# <a name="platformarray-class"></a>Platform::Array (Clase)

Representa una matriz unidimensional modificable que se puede recibir y pasar a través de la interfaz binaria de aplicación (ABI).

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Members

Platform:: Array hereda todos sus métodos de la [clase Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) e implementa la propiedad `Value` de la [interfaz Platform:: IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructores de matriz](#ctor)|Inicializa una matriz unidimensional modificable de tipos especificados por el parámetro de plantilla de clase, *T*.|

### <a name="methods"></a>Métodos

Consulte la [clase Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Propiedades

|||
|-|-|
|[Array:: Value](#value)|Recupera un identificador a la matriz actual.|

### <a name="remarks"></a>Observaciones

La clase Array está sellada y no se puede heredar.

El sistema de tipos de Windows Runtime no admite el concepto de matrices escalonadas y, por consiguiente, no se puede pasar un IVector < Platform:: Array\<T > > como un parámetro de método o valor devuelto. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.

Para obtener más información sobre cuándo y cómo usar Platform:: Array, vea [array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Esta clase se define en el encabezado de vccorlib.h, que se incluye automáticamente por el compilador. Es visible en IntelliSense pero no en Examinador de objetos porque no es un tipo público definido en Platform. winmd.

### <a name="requirements"></a>Requisitos

Opción del compilador: **/ZW**

## <a name="ctor"></a>Constructores de matriz

Inicializa una matriz unidimensional modificable de tipos especificados por el parámetro de plantilla de clase, *T*.

## <a name="syntax"></a>Sintaxis

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Parámetro de plantilla de clase.

*size*<br/>
Número de elementos de la matriz.

*data*<br/>
Un puntero a una matriz de datos de tipo `T` que se usa para inicializar este objeto Array.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo crear instancias de Platform:: Array, vea [array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>Array:: get (método)

Recupera una referencia al elemento de matriz en la ubicación de índice especificada.

## <a name="syntax"></a>Sintaxis

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parámetros

*índice*<br/>
Un índice basado en cero que identifica un elemento de la matriz. El índice mínimo es 0 y el índice máximo es el valor especificado por el parámetro `size` en el [constructor](#ctor)de la matriz.

### <a name="return-value"></a>Valor devuelto

El elemento de matriz especificado por el parámetro `index`.

## <a name="value"></a>Array:: Value (propiedad)

Recupera un identificador a la matriz actual.

## <a name="syntax"></a>Sintaxis

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Valor devuelto

Un identificador a la matriz actual.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)<br/>
[Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
