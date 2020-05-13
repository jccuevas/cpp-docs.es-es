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
ms.openlocfilehash: c49ceec72be62d8ff3125f04d97bbb6952501677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370975"
---
# <a name="max_none-class"></a>max_none (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima de cero.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*máximo*|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|

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

## <a name="max_noneallocated"></a><a name="allocated"></a>max_none::asignado

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

## <a name="max_nonedeallocated"></a><a name="deallocated"></a>max_none::dasignado

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

## <a name="max_nonefull"></a><a name="full"></a>max_none::completo

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

Esta función miembro siempre devuelve **true**.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la **true**llamada `deallocate` devuelve true , coloca el bloque de memoria en la lista libre; si devuelve **false**false `deallocate` , llama al operador **delete** para desasignar el bloque.

## <a name="max_nonereleased"></a><a name="released"></a>max_none::liberado

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Observaciones

Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="max_nonesaved"></a><a name="saved"></a>max_none::salvado

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Observaciones

Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
