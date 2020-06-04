---
title: max_variable_size (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: 79e37d8c464a009e4a5196aeacc8d4a718e355b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370964"
---
# <a name="max_variable_size-class"></a>max_variable_size (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima que es aproximadamente proporcional al número de bloques de memoria asignada.

## <a name="syntax"></a>Sintaxis

```cpp
class max_variable_size
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[max_variable_size](#max_variable_size)|Construye un objeto de tipo `max_variable_size`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[allocated](#allocated)|Aumenta el número de bloques de memoria asignada.|
|[desasignado](#deallocated)|Reduce el número de bloques de memoria asignada.|
|[Completo](#full)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|
|[Liberado](#released)|Reduce el número de bloques de memoria de la lista libre.|
|[saved](#saved)|Aumenta el número de bloques de memoria de la lista libre.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size::asignado

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Observaciones

Esta función *_Nx* miembro agrega _Nx `_Nallocs`al valor almacenado . Se llama a esta función `cache_freelist::allocate` miembro después de cada llamada correcta del operador **new**. El argumento *_Nx* es el número de bloques de memoria en el fragmento asignado por el operador **new**.

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size::dasignado

Reduce el número de bloques de memoria asignada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Observaciones

La función *_Nx* miembro resta `_Nallocs`_Nx del valor almacenado. Se llama a esta función miembro después de cada llamada de `cache_freelist::deallocate` operador **delete**. El argumento *_Nx* es el número de bloques de memoria en el fragmento desasignado por el operador **delete**.

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size::completo

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

**true** `_Nallocs / 16 + 16 <= _Nblocks`si .

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la **true**llamada `deallocate` devuelve true , coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **delete** para desasignar el bloque.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size::max_variable_size

Construye un objeto de tipo `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Observaciones

El constructor inicializa los valores almacenados `_Nblocks` y `_Nallocs` en cero.

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size::liberado

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Observaciones

Esta función miembro reduce el valor almacenado `_Nblocks`. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size::salvado

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Observaciones

Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
