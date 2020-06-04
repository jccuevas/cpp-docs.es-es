---
title: scheduler_worker_creation_error (clase)
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: e7f2763d7244be9e5e5b006b31b97c08e213a4f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142764"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error (clase)

Esta clase describe una excepción producida debido a un error al crear un contexto de ejecución del trabajo en el runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Sobrecargado. Construye un objeto `scheduler_worker_creation_error`.|

## <a name="remarks"></a>Observaciones

Normalmente, esta excepción se produce cuando se produce un error en una llamada al sistema operativo para crear contextos de ejecución desde el Runtime de simultaneidad. Los contextos de ejecución son subprocesos que ejecutan tareas en el Runtime de simultaneidad. El código de error que se devolvería normalmente de una llamada al método de Win32 `GetLastError` se convierte en un valor de tipo `HRESULT` y se puede recuperar mediante el método de la clase base `get_error_code`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>scheduler_worker_creation_error

Construye un objeto `scheduler_worker_creation_error`.

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

*_Hresult*<br/>
Valor `HRESULT` del error que produjo la excepción.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
