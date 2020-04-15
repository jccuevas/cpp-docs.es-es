---
title: lock_guard (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351714"
---
# <a name="lock_guard-class"></a>lock_guard (Clase)

Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Observaciones

El argumento de plantilla `Mutex` debe nombrar un *tipo de exclusión mutua*.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`lock_guard::mutex_type`|Sinónimo del argumento de plantilla `Mutex`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[lock_guard](#lock_guard)|Construye un objeto `lock_guard`.|
|[Destructor lock_guard::~lock_guard](#dtorlock_guard_destructor)|Desbloquea el objeto `mutex` que se pasó al constructor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de exclusión mutua

**Espacio de nombres:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>Constructor lock_guard::lock_guard

Construye un objeto `lock_guard`.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parámetros

*Mtx*\
Un objeto *de tipo mutex.*

### <a name="remarks"></a>Observaciones

El primer constructor construye un `lock_guard` objeto de tipo y bloquea *Mtx*. Si *Mtx* no es una exclusión mutua recursiva, debe desbloquearse cuando se llama a este constructor.

El segundo constructor no bloquea *Mtx*. *Mtx* debe estar bloqueado cuando se llama a este constructor. El constructor no inicia excepciones.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard::lock_guard Destructor

Desbloquea el objeto `mutex` que se pasó al constructor.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Observaciones

Si `mutex` no existe cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>de exclusión mutua](../standard-library/mutex.md)
