---
title: combinable (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60e1f944d19efd22cb2c6c7d6a3752d6d32ae1e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381678"
---
# <a name="combinable-class"></a>Clase combinable

El objeto `combinable<T>` está diseñado para proporcionar copias de subprocesos privados de datos, para realizar subcálculos de subprocesos locales sin bloqueos durante algoritmos paralelos. Al final de la operación paralela, los subcálculos de subprocesos privados pueden combinarse en un resultado final. Esta clase se puede utilizar en lugar de una variable compartida y puede dar lugar a una mejora en el rendimiento que, de lo contrario, daría lugar a mucha contención en esa variable compartida.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos del resultado combinado final. El tipo debe tener un constructor de copias y un constructor predeterminado.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[clase combinable](#ctor)|Sobrecargado. Construye un nuevo objeto `combinable`.|
|[~ combinable (destructor)](#dtor)|Destruye un objeto `combinable`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[clear](#clear)|Borra los resultados intermedios de cálculo de un uso anterior.|
|[combine](#combine)|Calcula un valor final del conjunto de subcálculos de subprocesos locales llamando al functor de combinación.|
|[combine_each](#combine_each)|Calcula un valor final del conjunto de subcálculos de subprocesos locales llamando al functor de combinación una vez por cada cálculo secundario local de subproceso. El resultado final se acumula por el objeto de función.|
|[local](#local)|Sobrecargado. Devuelve una referencia al cálculo secundario subprocesos privados.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Asigna a un `combinable` objeto desde otro `combinable` objeto.|

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`combinable`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="clear"></a> Borrar

Borra los resultados intermedios de cálculo de un uso anterior.

```
void clear();
```

##  <a name="ctor"></a> clase combinable

Construye un nuevo objeto `combinable`.

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
El tipo del objeto functor de inicialización.

*_FnInitialize*<br/>
Una función que se llamará para inicializar cada nuevo valor de subprocesos privados del tipo `T`. Debe admitir un operador de llamada de función con la firma `T ()`.

*_Copiar*<br/>
Existente `combinable` objeto que se copiará en ésta.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa nuevos elementos con el constructor predeterminado para el tipo `T`.

El segundo constructor inicializa nuevos elementos mediante el functor de inicialización proporcionado como el `_FnInitialize` parámetro.

El tercer constructor es el constructor de copias.

##  <a name="dtor"></a> ~ combinable

Destruye un objeto `combinable`.

```
~combinable();
```

##  <a name="combine"></a> combinar

Calcula un valor final del conjunto de subcálculos de subprocesos locales llamando al functor de combinación.

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
El tipo de objeto de función que se invocará para combinar dos subcálculos de subprocesos locales.

*_FnCombine*<br/>
El functor que se usa para combinar los cálculos secundarios. Su firma es `T (T, T)` o `T (const T&, const T&)`, y debe ser asociativa y conmutativa.

### <a name="return-value"></a>Valor devuelto

El resultado final de combinar todos los subcálculos de subprocesos privados.

##  <a name="combine_each"></a> combine_each

Calcula un valor final del conjunto de subcálculos de subprocesos locales llamando al functor de combinación una vez por cada cálculo secundario local de subproceso. El resultado final se acumula por el objeto de función.

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
El tipo de objeto de función que se invocará para combinar un cálculo de subdirectorio local de subproceso único.

*_FnCombine*<br/>
El functor que se usa para combinar un cálculo secundario. Su firma es `void (T)` o `void (const T&)`y debe ser asociativa y conmutativa.

##  <a name="local"></a> local

Devuelve una referencia al cálculo secundario subprocesos privados.

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parámetros

*_Exists*<br/>
Una referencia a un valor booleano. El valor booleano al que hace referencia este argumento se establecerá en `true` si el cálculo secundario ya existe en este subproceso y establece en `false` si éste era el primer cálculo secundario en este subproceso.

### <a name="return-value"></a>Valor devuelto

Una referencia al cálculo secundario subprocesos privados.

##  <a name="operator_eq"></a> operator=

Asigna a un `combinable` objeto desde otro `combinable` objeto.

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parámetros

*_Copiar*<br/>
Existente `combinable` objeto que se copiará en ésta.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `combinable` objeto.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
