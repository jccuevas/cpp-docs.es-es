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
ms.openlocfilehash: fbc4351297ab8a3cc90a2a77fa31c3b134f10eab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370994"
---
# <a name="max_unbounded-class"></a>max_unbounded (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que no limita la longitud máxima de un objeto [freelist](../standard-library/freelist-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a>max_unbounded::asignado

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Observaciones

Esta función miembro no hace nada. Se llama después de `cache_freelist::allocate` cada llamada exitosa por el operador **new**. El argumento *_Nx* es el número de bloques de memoria en el fragmento asignado por el operador **new**.

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a>max_unbounded::dasignado

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

## <a name="max_unboundedfull"></a><a name="full"></a>max_unbounded::completo

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

La función miembro siempre devuelve **false**.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la **true**llamada `deallocate` devuelve true , coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **delete** para desasignar el bloque.

## <a name="max_unboundedreleased"></a><a name="released"></a>max_unbounded::liberado

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Observaciones

Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="max_unboundedsaved"></a><a name="saved"></a>max_unbounded::salvado

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Observaciones

Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
