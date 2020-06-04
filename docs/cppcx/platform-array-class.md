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
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318655"
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

### <a name="members"></a>Miembros

Platform::Array hereda todos sus métodos de la clase `Value` [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) e implementa la propiedad de la [interfaz Platform::IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructores de matriz](#ctor)|Inicializa una matriz unidimensional y modificable de tipos especificados por el parámetro de plantilla de clase, *T*.|

### <a name="methods"></a>Métodos

Consulte [Platform::WriteOnlyArray (Clase)](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Propiedades

|||
|-|-|
|[Matriz::Valor](#value)|Recupera un identificador a la matriz actual.|

### <a name="remarks"></a>Observaciones

La clase Array está sellada y no se puede heredar.

El sistema de tipos de Windows Runtime no admite el concepto de matrices irregulares y, por lo tanto, no se puede pasar un IVector<Platform::Array\<T>> como un valor devuelto o parámetro de método. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.

Para obtener más información sobre cuándo y cómo utilizar Platform::Array, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Esta clase se define en el encabezado de vccorlib.h, que se incluye automáticamente por el compilador. Es visible en IntelliSense, pero no en el Examinador de objetos porque no es un tipo público definido en platform.winmd.

### <a name="requirements"></a>Requisitos

Opción del compilador: **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>Constructores de arreglos de discos

Inicializa una matriz unidimensional y modificable de tipos especificados por el parámetro de plantilla de clase, *T*.

## <a name="syntax"></a>Sintaxis

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Parámetro de plantilla de clase.

*Tamaño*<br/>
Número de elementos de la matriz.

*datos*<br/>
Un puntero a una matriz de datos de tipo `T` que se usa para inicializar este objeto Array.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo crear instancias de Platform::Array, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a>Array::get Método

Recupera una referencia al elemento de matriz en la ubicación de índice especificada.

## <a name="syntax"></a>Sintaxis

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parámetros

*índice*<br/>
Un índice basado en cero que identifica un elemento de la matriz. El índice mínimo es 0 y el índice `size` máximo es el valor especificado por el parámetro en el [constructor Array](#ctor).

### <a name="return-value"></a>Valor devuelto

El elemento de matriz especificado por el parámetro `index`.

## <a name="arrayvalue-property"></a><a name="value"></a>Array::Value (Propiedad)

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
