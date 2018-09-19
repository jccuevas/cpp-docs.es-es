---
title: Clase max_variable_size | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 974cee757708b9f7b1e48ea3bec3c4af98ced558
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957662"
---
# <a name="maxvariablesize-class"></a>max_variable_size (Clase)

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

|Función miembro|Descripción|
|-|-|
|[allocated](#allocated)|Aumenta el número de bloques de memoria asignada.|
|[deallocated](#deallocated)|Reduce el número de bloques de memoria asignada.|
|[full](#full)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|
|[released](#released)|Reduce el número de bloques de memoria de la lista libre.|
|[saved](#saved)|Aumenta el número de bloques de memoria de la lista libre.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocated"></a>  max_variable_size::allocated

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

Esta función miembro agrega *_Nx* al valor almacenado `_Nallocs`. Esta función miembro se llama después de cada llamada correcta por `cache_freelist::allocate` al operador **nuevo**. El argumento *_Nx* es el número de bloques de memoria del fragmento asignado por el operador **nuevo**.

## <a name="deallocated"></a>  max_variable_size::deallocated

Reduce el número de bloques de memoria asignada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

La función miembro resta *_Nx* del valor almacenado `_Nallocs`. Se llama a esta función miembro después de cada llamada por `cache_freelist::deallocate` al operador **eliminar**. El argumento *_Nx* es el número de bloques de memoria del fragmento desasignado por el operador **eliminar**.

## <a name="full"></a>  max_variable_size::full

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

**True** si `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve **true**, `deallocate` coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **eliminar** desasignar el bloque.

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

Construye un objeto de tipo `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Comentarios

El constructor inicializa los valores almacenados `_Nblocks` y `_Nallocs` en cero.

## <a name="released"></a>  max_variable_size::released

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Comentarios

Esta función miembro reduce el valor almacenado `_Nblocks`. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="saved"></a>  max_variable_size::saved

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentarios

Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
