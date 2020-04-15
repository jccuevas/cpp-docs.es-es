---
title: Platform::Collections::BackInsertIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: fcb680c8f43a50801d081762bb5b546cb110c52d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354768"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator (Clase)

Representa un iterador que inserta, en lugar de sobrescribir, elementos en el back-end de una colección secuencial.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de elemento de la colección actual.

### <a name="remarks"></a>Observaciones

La clase BackInsertIterator implementa las reglas requeridas por [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicializa una nueva instancia de la clase BackInsertIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[BackInsertIterator::operador* Operador](#operator-dereference)|Recupera una referencia al objeto BackInsertIterator actual.|
|[BackInsertIterator::operador++ Operador](#operator-increment)|Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.|
|[BackInsertIterator::operator= (Operador)](#operator-assign)|Anexa el objeto especificado al final de la colección secuencial actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BackInsertIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a>BackInsertIterator::BackInsertIterator Constructor

Inicializa una nueva instancia de la clase `BackInsertIterator`.

## <a name="syntax"></a>Sintaxis

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parámetros

*Ⅴ*<br/>
Un Objeto\<IVector T>.

### <a name="remarks"></a>Observaciones

Un objeto `BackInsertIterator` inserta elementos a continuación del último elemento del objeto especificado por el parámetro `v`.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a>BackInsertIterator::operador- Operador

Anexa el objeto especificado al final de la colección secuencial actual.

## <a name="syntax"></a>Sintaxis

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El objeto que se va a anexar a la colección actual.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto BackInsertIterator actual.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a>BackInsertIterator::operador* Operador

Recupera una referencia al objeto BackInsertIterator actual.

## <a name="syntax"></a>Sintaxis

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto BackInsertIterator actual.

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia al objeto BackInsertIterator actual, no así a ningún elemento de la colección actual.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a>BackInsertIterator::operador++ Operador

Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.

## <a name="syntax"></a>Sintaxis

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto BackInsertIterator actual.

### <a name="remarks"></a>Observaciones

Por diseño, el primero ejemplo de sintaxis incrementa previamente el objeto BackInsertIterator actual y el segundo lo incrementa posteriormente. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.

Sin embargo, este operador no modifica realmente el objeto BackInsertIterator. En su lugar, este operador devuelve una referencia al iterador actual sin modificar. Este es el mismo comportamiento que [operator*](#operator-dereference).

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
