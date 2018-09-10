---
title: 'Clase Platform:: Agile | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3745ead4fec8466df3f164c415b21d98f68c0ef7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109789"
---
# <a name="platformagile-class"></a>Platform::Agile (Clase)

Representa un objeto que tiene MashalingBehavior=Standard como objeto ágil, lo que reduce en gran medida las posibilidades de excepciones de subprocesamiento en tiempo de ejecución. `Agile<T>` permite que el objeto que no es Agile llame al mismo subproceso o a otro diferente, o que le llame a él. Para obtener más información, consulte [subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
typename de la clase que no es Agile.

### <a name="remarks"></a>Comentarios

La mayoría de las clases en el tiempo de ejecución de Windows es ágil. Un objeto Agile puede llamar a un objeto en proceso o fuera de proceso del mismo subproceso u otro diferente, o que le llame a él. Si un objeto no es Agile, ajuste el objeto que no Agile en un objeto `Agile<T>` , que es Agile. Se pueden calcular las referencias del objeto `Agile<T>` y se puede usar el objeto que no es Agile subyacente.

La clase `Agile<T>` es una clase de C++ estándar, nativa y requiere `agile.h`. Representa el objeto que no es Agile y el *contexto*del objeto Agile. El contexto especifica el modelo de subprocesos de un objeto Agile y el comportamiento del cálculo de referencias. El sistema operativo usa el contexto para determinar de qué manera calcular las referencias de un objeto.

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Agile](#ctor)|Inicializa una nueva instancia de la clase Agile.|
|[Agile::~Agile (Destructor)](#dtor)|Destruye la instancia actual de la clase Agile.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Agile::Get](#get)|Devuelve un identificador al objeto representado por el objeto Agile actual.|
|[Agile::GetAddressOf](#getaddressof)|Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Devuelve la dirección de un identificador al objeto representado por el objeto Agile actual.|
|[Agile::Release](#release)|Descarta el objeto y el contexto subyacentes del objeto Agile actual.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[Agile::operator->](#operator-arrow)|Recupera un identificador al objeto representado por el objeto Agile actual.|
|[Agile::operator=](#operator-assign)|Asigna el valor especificado al objeto Agile actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Object`

`Agile`

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Encabezado:** agile.h

## <a name="ctor"></a>  Constructor de Agile

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

### <a name="remarks"></a>Comentarios

La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia de Agile del objeto especificado por el parámetro `object`. La tercera versión es el constructor de copias. La cuarta versión es el constructor de movimiento. Este constructor no puede producir excepciones.

## <a name="dtor"></a>  Agile:: ~ Agile (destructor)

Destruye la instancia actual de la clase Agile.

## <a name="syntax"></a>Sintaxis

```cpp
~Agile();
```

### <a name="remarks"></a>Comentarios

Este destructor también libera el objeto representado por el objeto Agile actual.

## <a name="get"></a>   Método de Agile

Devuelve un identificador al objeto representado por el objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador al objeto representado por el objeto Agile actual.

El tipo del valor devuelto es realmente un tipo interno no revelado. Una manera cómoda de contener el valor devuelto es asignarlo a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myAgileTvariable->Get();`.

## <a name="getaddressof"></a>  Getaddressof (método)

Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.

## <a name="syntax"></a>Sintaxis

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo especificado por el parámetro typename de la plantilla.

### <a name="return-value"></a>Valor devuelto

La dirección de un identificador a un objeto de tipo `T`.

### <a name="remarks"></a>Comentarios

Esta operación libera la representación actual de un objeto de tipo `T`, si las hay; reinicializa los miembros de datos del objeto Agile; adquiere el contexto del subproceso actual; y, a continuación, devuelve la dirección de una variable de objeto de identificador que puede representar un objeto no ágil. Para hacer que una instancia de la clase ágil representar un objeto, utilice el operador de asignación ([Agile:: operator =](#operator-assign)) para asignar el objeto a la instancia de la clase Agile.

## <a name="getaddressofforinout"></a>  Getaddressofforinout (método)

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

### <a name="remarks"></a>Comentarios

Esta operación adquiere el contexto de subprocesos actual y devuelve después la dirección de un identificador al objeto subyacente.

## <a name="release"></a>  Método de Agile

Descarta el objeto y el contexto subyacentes del objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
void Release() throw();
```

### <a name="remarks"></a>Comentarios

Si existen, el objeto y el contexto subyacentes del objeto Agile actual se descartan y, a continuación, el valor del objeto Agile se establece en null.

## <a name="operator-arrow"></a>  Agile:: operator -&gt; operador

Recupera un identificador al objeto representado por el objeto Agile actual.

## <a name="syntax"></a>Sintaxis

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador al objeto representado por el objeto Agile actual.

Este operador devuelve realmente un tipo interno no revelado. Una manera cómoda de contener el valor devuelto es asignarlo a una variable que se declara con el **automática** palabra clave de deducción de tipos.

## <a name="operator-assign"></a>  Agile:: operator = (operador)

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

*LP*<br/>
Puntero de interfaz IUnknown de un objeto.

### <a name="return-value"></a>Valor devuelto

Identificador para un objeto de tipo `T`.

### <a name="remarks"></a>Comentarios

La primera versión del operador de asignación copia un identificador para un tipo de referencia al objeto Agile actual. La segunda versión copia una referencia a un tipo Agile al objeto Agile actual. La tercera versión mueve un tipo Agile al objeto Agile actual. La cuarta versión mueve un puntero a un objeto COM al objeto Agile actual.

La operación de asignación conserva automáticamente el contexto del objeto Agile actual.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)