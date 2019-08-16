---
title: max_unbounded (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: cea2f09837e5efc6969e4ab305d106b9c9728412
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447211"
---
# <a name="maxunbounded-class"></a>max_unbounded (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que no limita la longitud máxima de un objeto [freelist](../standard-library/freelist-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>  max_unbounded::allocated

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

## <a name="deallocated"></a>  max_unbounded::deallocated

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

## <a name="full"></a>  max_unbounded::full

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

La función miembro siempre devuelve **false**.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve **true**, `deallocate` coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **Delete** para desasignar el bloque.

## <a name="released"></a>  max_unbounded::released

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Comentarios

Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="saved"></a>  max_unbounded::saved

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentarios

Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
