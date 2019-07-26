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
ms.openlocfilehash: bbc39a169f9a4bbac3e78b208b3a1a31e4e30ff2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456376"
---
# <a name="maxfixedsize-class"></a>max_fixed_size (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Max*|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[max_fixed_size](#max_fixed_size)|Construye un objeto de tipo `max_fixed_size`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[allocated](#allocated)|Aumenta el número de bloques de memoria asignada.|
|[deallocated](#deallocated)|Reduce el número de bloques de memoria asignada.|
|[full](#full)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|
|[released](#released)|Reduce el número de bloques de memoria de la lista libre.|
|[saved](#saved)|Aumenta el número de bloques de memoria de la lista libre.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocated"></a>  max_fixed_size::allocated

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

La función miembro no hace nada. Se llama a esta función miembro después de cada llamada `cache_freelist::allocate` correcta por al operador **New**. El argumento *_Nx* es el número de bloques de memoria del fragmento asignado por el operador **New**.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Reduce el número de bloques de memoria asignada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

La función miembro no hace nada. Se llama a esta función miembro después de cada `cache_freelist::deallocate` llamada realizada por al operador **Delete**. El argumento *_Nx* es el número de bloques de memoria del fragmento desasignados por el operador **Delete**.

## <a name="full"></a>  max_fixed_size::full

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

**true** si `Max <= _Nblocks`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve **true**, `deallocate` coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **Delete** para desasignar el bloque.

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

Construye un objeto de tipo `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Comentarios

Este constructor inicializa el valor almacenado `_Nblocks` en cero.

## <a name="released"></a>  max_fixed_size::released

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Comentarios

Disminuye el valor almacenado `_Nblocks`. La función miembro `released` de la [clase máxima](../standard-library/allocators-header.md) actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="saved"></a>  max_fixed_size::saved

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentarios

Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
