---
title: Platform::ArrayReference (Clase)
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: f7e587902f1c99b294ed79255397aeffccee26b5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587929"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference (Clase)

`ArrayReference` es un tipo de optimización que puedes usar en lugar de [Platform::Array^](../cppcx/platform-array-class.md) en parámetros de entrada cuando desees rellenar una matriz de estilo C con los datos de entrada.

## <a name="syntax"></a>Sintaxis

```cpp
class ArrayReference
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[ArrayReference:: ArrayReference](#ctor)|Inicializa una nueva instancia de la clase `ArrayReference`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[ArrayReference::operator() (Operador)](#operator-call)|Convierte este `ArrayReference` en `Platform::Array<T>^*`.|
|[ArrayReference::operator= (Operador)](#operator-assign)|Asigna el contenido de otro `ArrayReference` a esta instancia.|

## <a name="exceptions"></a>Excepciones

### <a name="remarks"></a>Comentarios

Si usas `ArrayReference` para rellenar una matriz de estilo C, evitas la operación de copia adicional que sería necesaria para copiar primero a una variable `Platform::Array` y después a la matriz de estilo C. Cuando usas `ArrayReference`, solo se realiza una operación de copia. Para obtener un ejemplo de código, vea [array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Encabezado:** vccorlib.h

## <a name="ctor"></a>ArrayReference:: ArrayReference (constructor)

Inicializa una nueva instancia de la clase [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) .

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

### <a name="remarks"></a>Comentarios

## <a name="operator-assign"></a>ArrayReference:: Operator = (operador)

Asigna el objeto especificado al objeto [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) actual mediante la semántica de movimiento.

### <a name="syntax"></a>Sintaxis

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parámetros

*otherArg*<br/>
Objeto que se mueve al objeto `ArrayReference` actual.

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto de tipo `ArrayReference`.

### <a name="remarks"></a>Comentarios

`Platform::ArrayReference` es una plantilla de clase estándar de C++, no una clase de referencia.

## <a name="operator-call"></a>ArrayReference:: Operator () (operador)

Vuelve a convertir el objeto [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) actual en una clase [Platform:: Array](../cppcx/platform-array-class.md) .

### <a name="syntax"></a>Sintaxis

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Valor devuelto

Identificador a objeto de tipo `Array<TArg>^`.

### <a name="remarks"></a>Comentarios

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) es una plantilla C++ de clase estándar y [Platform:: Array](../cppcx/platform-array-class.md) es una clase Ref.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
