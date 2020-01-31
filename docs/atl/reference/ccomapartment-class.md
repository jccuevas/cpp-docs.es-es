---
title: Clase CComApartment
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821680"
---
# <a name="ccomapartment-class"></a>Clase CComApartment

Esta clase proporciona compatibilidad para administrar un contenedor en un módulo EXE agrupado por subprocesos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComApartment
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|Marca la dirección de inicio del subproceso.|
|[CComApartment::GetLockCount](#getlockcount)|Devuelve el recuento de bloqueos actual del subproceso.|
|[CComApartment::Lock](#lock)|Incrementa el recuento de bloqueos del subproceso.|
|[CComApartment::Unlock](#unlock)|Disminuye el recuento de bloqueos del subproceso.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contiene el identificador del subproceso.|
|[CComApartment::m_hThread](#m_hthread)|Contiene el identificador del subproceso.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contiene el recuento de bloqueos actual del subproceso.|

## <a name="remarks"></a>Notas

[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) usa `CComApartment` para administrar un apartamento en un módulo exe agrupado por subprocesos. `CComApartment` proporciona métodos para aumentar y disminuir el número de bloqueos en un subproceso.

## <a name="requirements"></a>Requisitos de

**Encabezado:** ATLBase. h

##  <a name="apartment"></a>  CComApartment::Apartment

Marca la dirección de inicio del subproceso.

```
DWORD Apartment();
```

### <a name="return-value"></a>Valor devuelto

Siempre es 0.

### <a name="remarks"></a>Notas

Se establece automáticamente durante [CComAutoThreadModule:: init](../../atl/reference/ccomautothreadmodule-class.md#init).

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

El constructor.

```
CComApartment();
```

### <a name="remarks"></a>Notas

Inicializa los miembros de datos de `CComApartment` [m_nLockCnt](#m_nlockcnt) y [m_hThread](#m_hthread).

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

Devuelve el recuento de bloqueos actual del subproceso.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Valor devuelto

Recuento de bloqueos en el subproceso.

##  <a name="lock"></a>  CComApartment::Lock

Incrementa el recuento de bloqueos del subproceso.

```
LONG Lock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Notas

Llamado por [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

El recuento de bloqueos en el subproceso se usa para fines estadísticos.

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

Contiene el identificador del subproceso.

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>  CComApartment::m_hThread

Contiene el identificador del subproceso.

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt

Contiene el recuento de bloqueos actual del subproceso.

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

Disminuye el recuento de bloqueos del subproceso.

```
LONG Unlock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Notas

Llamado por [CComAutoThreadModule:: Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

El recuento de bloqueos en el subproceso se usa para fines estadísticos.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
