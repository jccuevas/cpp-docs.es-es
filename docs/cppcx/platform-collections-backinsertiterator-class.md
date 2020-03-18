---
title: Platform::Collections::BackInsertIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 79854d8ead089aeba88fbdc151fdc0788dd181c1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445783"
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

### <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[BackInsertIterator:: BackInsertIterator](#ctor)|Inicializa una nueva instancia de la clase BackInsertIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[BackInsertIterator::operator* (Operador)](#operator-dereference)|Recupera una referencia al objeto BackInsertIterator actual.|
|[BackInsertIterator::operator++ (Operador)](#operator-increment)|Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.|
|[BackInsertIterator::operator= (Operador)](#operator-assign)|Anexa el objeto especificado al final de la colección secuencial actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BackInsertIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="ctor"></a>BackInsertIterator:: BackInsertIterator (constructor)

Inicializa una nueva instancia de la clase `BackInsertIterator`.

## <a name="syntax"></a>Sintaxis

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parámetros

*v*<br/>
Objeto de > IVector\<T.

### <a name="remarks"></a>Observaciones

Un objeto `BackInsertIterator` inserta elementos a continuación del último elemento del objeto especificado por el parámetro `v`.

## <a name="operator-assign"></a>BackInsertIterator:: Operator = (operador)

Anexa el objeto especificado al final de la colección secuencial actual.

## <a name="syntax"></a>Sintaxis

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parámetros

*t*<br/>
El objeto que se va a anexar a la colección actual.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto BackInsertIterator actual.

## <a name="operator-dereference"></a>BackInsertIterator:: Operator * (operador)

Recupera una referencia al objeto BackInsertIterator actual.

## <a name="syntax"></a>Sintaxis

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto BackInsertIterator actual.

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia al objeto BackInsertIterator actual, no así a ningún elemento de la colección actual.

## <a name="operator-increment"></a>BackInsertIterator:: Operator + + (operador)

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

Sin embargo, este operador no modifica realmente el objeto BackInsertIterator. En su lugar, este operador devuelve una referencia al iterador actual sin modificar. Este es el mismo comportamiento que el [operador *](#operator-dereference).

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
