---
title: Clase lock_guard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f53732fee62906da19a5771c8598cce51fc6331
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953763"
---
# <a name="lockguard-class"></a>lock_guard (Clase)

Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Comentarios

El argumento de plantilla `Mutex` debe nombrar un *tipo de exclusión mutua*.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`lock_guard::mutex_type`|Sinónimo del argumento de plantilla `Mutex`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[lock_guard](#lock_guard)|Construye un objeto `lock_guard`.|
|[Destructor lock_guard::~lock_guard](#dtorlock_guard_destructor)|Desbloquea el objeto `mutex` que se pasó al constructor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="lock_guard"></a>  Constructor lock_guard::lock_guard

Construye un objeto `lock_guard`.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parámetros

*Mtx* A *tipo de exclusión mutua* objeto.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto de tipo `lock_guard` y bloqueos *Mtx*. Si *Mtx* no es una exclusión mutua recursiva, debe estar desbloqueado cuando se llama a este constructor.

El segundo constructor no bloquea *Mtx*. *Mtx* debe estar bloqueado cuando se llama a este constructor. El constructor no inicia excepciones.

## <a name="dtorlock_guard_destructor"></a>  Destructor lock_guard::~lock_guard

Desbloquea el objeto `mutex` que se pasó al constructor.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Comentarios

Si `mutex` no existe cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
