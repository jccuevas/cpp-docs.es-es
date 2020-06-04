---
title: Platform::ArrayReference (Clase)
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354788"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference (Clase)

`ArrayReference` es un tipo de optimización que puedes usar en lugar de [Platform::Array^](../cppcx/platform-array-class.md) en parámetros de entrada cuando desees rellenar una matriz de estilo C con los datos de entrada.

## <a name="syntax"></a>Sintaxis

```cpp
class ArrayReference
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Inicializa una nueva instancia de la clase `ArrayReference`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[ArrayReference::operator() Operador](#operator-call)|Convierte este `ArrayReference` en `Platform::Array<T>^*`.|
|[ArrayReference::operator= (Operador)](#operator-assign)|Asigna el contenido de otro `ArrayReference` a esta instancia.|

## <a name="exceptions"></a>Excepciones

### <a name="remarks"></a>Observaciones

Si usas `ArrayReference` para rellenar una matriz de estilo C, evitas la operación de copia adicional que sería necesaria para copiar primero a una variable `Platform::Array` y después a la matriz de estilo C. Cuando usas `ArrayReference`, solo se realiza una operación de copia. Para obtener un ejemplo de código, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Encabezado:** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>ArrayReference::ArrayReference Constructor

Inicializa una nueva instancia de la clase [Platform::ArrayReference.](../cppcx/platform-arrayreference-class.md)

### <a name="syntax"></a>Sintaxis

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parámetros

*dataArg*<br/>
Puntero a los datos de matriz.

*sizeArg*<br/>
Número de elementos de la matriz de origen.

*otherArg*<br/>
Objeto `ArrayReference` cuyos datos se moverán para inicializar la nueva instancia.

### <a name="remarks"></a>Observaciones

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>ArrayReference::operador- Operador

Asigna el objeto especificado al objeto [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) actual mediante la semántica de movimiento.

### <a name="syntax"></a>Sintaxis

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parámetros

*otherArg*<br/>
Objeto que se mueve al objeto `ArrayReference` actual.

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto de tipo `ArrayReference`.

### <a name="remarks"></a>Observaciones

`Platform::ArrayReference` es una plantilla de clase estándar de C++, no una clase de referencia.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>ArrayReference::operator() Operador

Convierte el objeto [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) actual en una clase [Platform::Array.](../cppcx/platform-array-class.md)

### <a name="syntax"></a>Sintaxis

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Valor devuelto

Identificador a objeto de tipo `Array<TArg>^`.

### <a name="remarks"></a>Observaciones

[Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) es una plantilla de clase C++ estándar y [Platform::Array](../cppcx/platform-array-class.md) es una clase ref.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
