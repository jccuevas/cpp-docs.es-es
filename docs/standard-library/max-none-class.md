---
title: max_none (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: 0d409928de4bf66bcc6d6dda3008131f87e790c3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460169"
---
# <a name="maxnone-class"></a>max_none (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima de cero.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Max*|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|

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

## <a name="allocated"></a>  max_none::allocated

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

Esta función miembro no hace nada. Se llama después de cada llamada correcta por `cache_freelist::allocate` al operador **New**. El argumento *_Nx* es el número de bloques de memoria del fragmento asignado por el operador **New**.

## <a name="deallocated"></a>  max_none::deallocated

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

## <a name="full"></a>  max_none::full

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

Esta función miembro siempre devuelve **true**.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve **true**, `deallocate` coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **Delete** para desasignar el bloque.

## <a name="released"></a>  max_none::released

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Comentarios

Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="saved"></a>  max_none::saved

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentarios

Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
