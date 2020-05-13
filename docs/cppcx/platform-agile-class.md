---
title: Platform::Agile (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 0822cef10b199a5bc3b33f116065816e380bf8a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376502"
---
# <a name="platformagile-class"></a>Platform::Agile (Clase)

Representa un objeto que tiene MashalingBehavior=Standard como objeto ágil, lo que reduce en gran medida las posibilidades de excepciones de subprocesamiento en tiempo de ejecución. `Agile<T>` permite que el objeto que no es Agile llame al mismo subproceso o a otro diferente, o que le llame a él. Para obtener más información, consulte [Subprocesos y cálculo](../cppcx/threading-and-marshaling-c-cx.md)de referencias .

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
typename de la clase que no es Agile.

### <a name="remarks"></a>Observaciones

La mayoría de las clases de Windows Runtime son ágiles. Un objeto Agile puede llamar a un objeto en proceso o fuera de proceso del mismo subproceso u otro diferente, o que le llame a él. Si un objeto no es Agile, ajuste el objeto que no Agile en un objeto `Agile<T>` , que es Agile. Se pueden calcular las referencias del objeto `Agile<T>` y se puede usar el objeto que no es Agile subyacente.

La clase `Agile<T>` es una clase de C++ estándar, nativa y requiere `agile.h`. Representa el objeto que no es Agile y el *contexto*del objeto Agile. El contexto especifica el modelo de subprocesos de un objeto Agile y el comportamiento del cálculo de referencias. El sistema operativo usa el contexto para determinar de qué manera calcular las referencias de un objeto.

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Agile::Agile](#ctor)|Inicializa una nueva instancia de la clase Agile.|
|[Agile::~Agile (Destructor)](#dtor)|Destruye la instancia actual de la clase Agile.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Agile::Get](#get)|Devuelve un identificador al objeto representado por el objeto Agile actual.|
|[Agile::GetAddressOf](#getaddressof)|Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Devuelve la dirección de un identificador al objeto representado por el objeto Agile actual.|
|[Agile::Release](#release)|Descarta el objeto y el contexto subyacentes del objeto Agile actual.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Agile::operador->](#operator-arrow)|Recupera un identificador al objeto representado por el objeto Agile actual.|
|[Agile::operator=](#operator-assign)|Asigna el valor especificado al objeto Agile actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Object`

`Agile`

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Encabezado:** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Agile::Constructor ágil

Inicializa una nueva instancia de la clase Agile.

## <a name="syntax"></a>Sintaxis

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo especificado por el parámetro typename de la plantilla.

*object*<br/>
En la segunda versión de este constructor, un objeto utilizado para inicializar una nueva instancia de Agile. En la tercera versión, el objeto que se copia en la nueva instancia de Agile. En la cuarta versión, el objeto que se mueve a la nueva instancia de Agile.

### <a name="remarks"></a>Observaciones

La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia de Agile del objeto especificado por el parámetro `object`. La tercera versión es el constructor de copias. La cuarta versión es el constructor de movimiento. Este constructor no puede producir excepciones.

## <a name="agileagile-destructor"></a><a name="dtor"></a>Agile::-Agile Destructor

Destruye la instancia actual de la clase Agile.

## <a name="syntax"></a>Sintaxis

```cpp
~Agile();
```

### <a name="remarks"></a>Observaciones

Este destructor también libera el objeto representado por el objeto Agile actual.

## <a name="agileget-method"></a><a name="get"></a>Agile::Get Método

Devuelve un identificador al objeto representado por el objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador al objeto representado por el objeto Agile actual.

El tipo del valor devuelto es realmente un tipo interno no revelado. Una forma cómoda de contener el valor devuelto es asignarlo a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo, `auto x = myAgileTvariable->Get();`.

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile::GetAddressOf Método

Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.

## <a name="syntax"></a>Sintaxis

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo especificado por el parámetro typename de la plantilla.

### <a name="return-value"></a>Valor devuelto

Dirección de un identificador para un objeto de tipo `T`.

### <a name="remarks"></a>Observaciones

Esta operación libera la representación actual de un objeto de tipo `T`, en caso de haberlo; reinicializa los miembros de datos del objeto Agile; adquiere el contexto de subprocesos actual; y luego devuelve la dirección de una variable de controlador a objeto que puede representar un objeto que no es Agile. Para hacer que una instancia de clase Agile represente un objeto, utilice el operador de asignación ([Agile::operator )](#operator-assign)para asignar el objeto a la instancia de clase Agile.

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Método Agile::GetAddressOfForInOut

Devuelve la dirección de un identificador al objeto representado por el objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo especificado por el parámetro typename de la plantilla.

### <a name="return-value"></a>Valor devuelto

La dirección de un identificador al objeto representado por el objeto Agile actual.

### <a name="remarks"></a>Observaciones

Esta operación adquiere el contexto de subprocesos actual y devuelve después la dirección de un identificador al objeto subyacente.

## <a name="agilerelease-method"></a><a name="release"></a>Agile::Método de liberación

Descarta el objeto y el contexto subyacentes del objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
void Release() throw();
```

### <a name="remarks"></a>Observaciones

Si existen, el objeto y el contexto subyacentes del objeto Agile actual se descartan y, a continuación, el valor del objeto Agile se establece en null.

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Agile::operador-&gt; Operador

Recupera un identificador al objeto representado por el objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador al objeto representado por el objeto Agile actual.

Este operador devuelve realmente un tipo interno no revelado. Una forma cómoda de contener el valor devuelto es asignarlo a una variable que se declara con la palabra clave de deducción de tipo **automático.**

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Agile::operador- Operador

Asigna el objeto especificado al objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo especificado por el nombre de tipo de plantilla.

*object*<br/>
Objeto o identificador de un objeto que se copia o se mueve al objeto Agile actual.

*Lp*<br/>
Puntero de interfaz IUnknown de un objeto.

### <a name="return-value"></a>Valor devuelto

Identificador para un objeto de tipo `T`.

### <a name="remarks"></a>Observaciones

La primera versión del operador de asignación copia un identificador para un tipo de referencia al objeto Agile actual. La segunda versión copia una referencia a un tipo Agile al objeto Agile actual. La tercera versión mueve un tipo Agile al objeto Agile actual. La cuarta versión mueve un puntero a un objeto COM al objeto Agile actual.

La operación de asignación conserva automáticamente el contexto del objeto Agile actual.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
