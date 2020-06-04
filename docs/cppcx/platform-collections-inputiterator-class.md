---
title: Platform::Collections::InputIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354562"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator (Clase)

Proporciona un InputIterator de biblioteca de plantillas estándar para colecciones derivadas de Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
El typename de la clase de plantilla InputIterator.

### <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|
|`iterator_category`|La categoría de un iterador de entrada (::std::input_iterator_tag).|
|`pointer`|Puntero a `const X`|
|`reference`|Referencia a `const X`|
|`value_type`|El typename `X` .|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|Inicializa una nueva instancia de la clase InputIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[InputIterator::operator!= (Operador)](#operator-inequality)|Indica si el objeto InputIterator actual no es igual a un objeto InputIterator especificado.|
|[InputIterator::operador* Operador](#operator-dereference)|Recupera una referencia al elemento especificado por el objeto InputIterator actual.|
|[InputIterator::operador++ Operador](#operator-increment)|Incrementa el objeto InputIterator actual.|
|[InputIterator::operador - Operador](#operator-equality)|Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.|
|[InputIterator::operador-> Operador](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto InputIterator actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InputIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator::InputIterator Constructor

Inicializa una nueva instancia de la clase InputIterator.

### <a name="syntax"></a>Sintaxis

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parámetros

*Iterador*<br/>
Objeto de iterador.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator::operador-&gt; Operador

Recupera la dirección del elemento especificado por el objeto InputIterator actual.

### <a name="syntax"></a>Sintaxis

```
pointer operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Dirección del elemento especificado por el objeto InputIterator actual.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator::operador\* Operador

Recupera una referencia al elemento especificado por el objeto InputIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El elemento especificado por el objeto InputIterator actual.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator::operador - Operador

Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto InputIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el InputIterator actual es igual a *otro*; de lo contrario, **false**.

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator::operador++ Operador

Incrementa el objeto InputIterator actual.

### <a name="syntax"></a>Sintaxis

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis incrementa y devuelve después el objeto InputIterator actual. La segunda sintaxis devuelve una copia del objeto InputIterator actual e incrementa después el objeto InputIterator actual.

### <a name="remarks"></a>Observaciones

Lo primera sintaxis de InputIterator incrementa previamente el objeto InputIterator actual.

La segunda sintaxis incrementa posteriormente el objeto InputIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator::operator!

Indica si el objeto InputIterator actual no es igual a un objeto InputIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto InputIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el InputIterator actual no es igual a *otro*; de lo contrario, **false**.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
