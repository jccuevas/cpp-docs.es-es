---
title: scheduler_resource_allocation_error (clase)
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 2955320b443fb61f26d9f07ca336a45c620e2aa9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143337"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error (clase)

Esta clase describe una excepción que se produce debido a un error al adquirir un recurso crítico en el runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Sobrecargado. Construye un objeto `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_error_code](#get_error_code)|Devuelve el código de error que produjo la excepción.|

## <a name="remarks"></a>Observaciones

Normalmente, esta excepción se produce cuando se produce un error en una llamada al sistema operativo desde el Runtime de simultaneidad. El código de error que se devolvería normalmente de una llamada al método de Win32 `GetLastError` se convierte en un valor de tipo `HRESULT` y se puede recuperar mediante el método `get_error_code`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="get_error_code"></a>get_error_code

Devuelve el código de error que produjo la excepción.

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valor devuelto

Valor `HRESULT` del error que produjo la excepción.

## <a name="ctor"></a>scheduler_resource_allocation_error

Construye un objeto `scheduler_resource_allocation_error`.

```cpp
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

*_Hresult*<br/>
Valor `HRESULT` del error que produjo la excepción.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
