---
title: max_fixed_size (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371004"
---
# <a name="max_fixed_size-class"></a>max_fixed_size (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*máximo*|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[max_fixed_size](#max_fixed_size)|Construye un objeto de tipo `max_fixed_size`.|

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

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::asignado

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Observaciones

La función miembro no hace nada. Se llama a esta función `cache_freelist::allocate` miembro después de cada llamada correcta del operador **new**. El argumento *_Nx* es el número de bloques de memoria en el fragmento asignado por el operador **new**.

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::dasignado

Reduce el número de bloques de memoria asignada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Observaciones

La función miembro no hace nada. Se llama a esta función miembro después de cada llamada de `cache_freelist::deallocate` operador **delete**. El argumento *_Nx* es el número de bloques de memoria en el fragmento desasignado por el operador **delete**.

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::completo

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

**true** `Max <= _Nblocks`si ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la **true**llamada `deallocate` devuelve true , coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **delete** para desasignar el bloque.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Construye un objeto de tipo `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Observaciones

Este constructor inicializa el valor almacenado `_Nblocks` en cero.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::liberado

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Observaciones

Disminuye el valor almacenado `_Nblocks`. Cada `released` `cache_freelist::allocate` vez que quita un bloque de memoria de la lista gratuita, se llama a la función miembro de la [clase max](../standard-library/allocators-header.md) actual.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::salvado

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Observaciones

Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
