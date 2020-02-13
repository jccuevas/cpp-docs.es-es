---
title: combinable (clase)
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141432"
---
# <a name="combinable-class"></a>combinable (clase)

El objeto `combinable<T>` está diseñado para proporcionar copias de subprocesos privados de datos, para realizar subcálculos de subprocesos locales sin bloqueos durante algoritmos paralelos. Al final de la operación paralela, los subcálculos de subprocesos privados pueden combinarse en un resultado final. Esta clase se puede utilizar en lugar de una variable compartida y puede dar lugar a una mejora en el rendimiento que, de lo contrario, daría lugar a mucha contención en esa variable compartida.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos del resultado combinado final. El tipo debe tener un constructor de copias y un constructor predeterminado.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[combinable](#ctor)|Sobrecargado. Construye un nuevo objeto `combinable`.|
|[~ (destructor combinable)](#dtor)|Destruye un objeto `combinable`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[clear](#clear)|Borra los resultados de cálculo intermedios de un uso anterior.|
|[combine](#combine)|Calcula un valor final a partir del conjunto de subcálculos locales de subprocesos llamando al functor de combinación proporcionado.|
|[combine_each](#combine_each)|Calcula un valor final a partir del conjunto de subprocesos locales para el subproceso llamando al functor de combinación proporcionado una vez por subcálculo local del subproceso. El resultado final lo acumula el objeto de función.|
|[local](#local)|Sobrecargado. Devuelve una referencia al subcálculo privado del subproceso.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Asigna a un objeto `combinable` de otro objeto `combinable`.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Parallel containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`combinable`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="clear"></a>claridad

Borra los resultados de cálculo intermedios de un uso anterior.

```cpp
void clear();
```

## <a name="ctor"></a>combinable

Construye un nuevo objeto `combinable`.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto functor de inicialización.

*_FnInitialize*<br/>
Función a la que se llamará para inicializar cada nuevo valor de subproceso privado del tipo `T`. Debe admitir un operador de llamada de función con la firma `T ()`.

*_Copy*<br/>
Objeto de `combinable` existente que se va a copiar en este.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa nuevos elementos con el constructor predeterminado para el tipo `T`.

El segundo constructor inicializa nuevos elementos mediante el functor de inicialización proporcionado como `_FnInitialize` parámetro.

El tercer constructor es el constructor de copias.

## <a name="dtor"></a>~ combinable

Destruye un objeto `combinable`.

```cpp
~combinable();
```

## <a name="combine"></a>Combínelo

Calcula un valor final a partir del conjunto de subcálculos locales de subprocesos llamando al functor de combinación proporcionado.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se invocará para combinar dos subcálculos locales de subproceso.

*_FnCombine*<br/>
El functor que se usa para combinar los subprocesos. Su firma es `T (T, T)` o `T (const T&, const T&)`y debe ser asociativa y conmutativa.

### <a name="return-value"></a>Valor devuelto

Resultado final de la combinación de todos los subcálculos privados de subprocesos.

## <a name="combine_each"></a>combine_each

Calcula un valor final a partir del conjunto de subprocesos locales para el subproceso llamando al functor de combinación proporcionado una vez por subcálculo local del subproceso. El resultado final lo acumula el objeto de función.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se invocará para combinar un subcálculo único de subproceso local.

*_FnCombine*<br/>
El functor que se usa para combinar un subcálculo. Su firma es `void (T)` o `void (const T&)`y debe ser asociativa y conmutativa.

## <a name="local"></a>localizar

Devuelve una referencia al subcálculo privado del subproceso.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parámetros

*_Exists*<br/>
Referencia a un valor booleano. El valor booleano al que hace referencia este argumento se establecerá en **true** si el subcálculo ya existía en este subproceso y se establecerá en **false** si este era el primer subcálculo de este subproceso.

### <a name="return-value"></a>Valor devuelto

Referencia al subcálculo privado del subproceso.

## <a name="operator_eq"></a>operador =

Asigna a un objeto `combinable` de otro objeto `combinable`.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parámetros

*_Copy*<br/>
Objeto de `combinable` existente que se va a copiar en este.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `combinable`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
