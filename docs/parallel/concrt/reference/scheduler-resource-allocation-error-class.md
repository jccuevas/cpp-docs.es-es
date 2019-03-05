---
title: scheduler_resource_allocation_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 7f7254306253aabc33f46694f3da16734e6efccf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276499"
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error (Clase)

Esta clase describe una excepción que se produce debido a un error al adquirir un recurso crítico en el runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Sobrecargado. Construye un objeto `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_error_code](#get_error_code)|Devuelve el código de error que provocó la excepción.|

## <a name="remarks"></a>Comentarios

Esta excepción se produce normalmente cuando se produce un error en una llamada al sistema operativo desde el Runtime de simultaneidad. El código de error que se devolvería normalmente una llamada al método Win32 `GetLastError` se convierte en un valor de tipo `HRESULT` y se puede recuperar mediante el `get_error_code` método.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="get_error_code"></a> get_error_code

Devuelve el código de error que provocó la excepción.

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valor devuelto

El `HRESULT` valor del error que provocó la excepción.

##  <a name="ctor"></a> scheduler_resource_allocation_error

Construye un objeto `scheduler_resource_allocation_error`.

```
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
El `HRESULT` valor del error que provocó la excepción.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
