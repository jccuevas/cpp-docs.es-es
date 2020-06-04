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
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321120"
---
# <a name="ccomapartment-class"></a>Clase CComApartment

Esta clase proporciona compatibilidad para administrar un apartamento en un módulo EXE agrupado por subprocesos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComApartment
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComApartment::Apartamento](#apartment)|Marca la dirección inicial del subproceso.|
|[CComApartment::GetLockCount](#getlockcount)|Devuelve el recuento de bloqueos actual del subproceso.|
|[CComApartment::Bloqueo](#lock)|Incrementa el recuento de bloqueos del subproceso.|
|[CComApartment::Desbloquear](#unlock)|Disminuye el recuento de bloqueos del subproceso.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contiene el identificador del subproceso.|
|[CComApartment::m_hThread](#m_hthread)|Contiene el identificador del subproceso.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contiene el recuento de bloqueos actual del subproceso.|

## <a name="remarks"></a>Observaciones

`CComApartment`[cComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) utiliza para administrar un apartamento en un módulo EXE agrupado por subprocesos. `CComApartment`proporciona métodos para incrementar y disminuir el recuento de bloqueos en un subproceso.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CComApartment::Apartamento

Marca la dirección inicial del subproceso.

```
DWORD Apartment();
```

### <a name="return-value"></a>Valor devuelto

Siempre es 0.

### <a name="remarks"></a>Observaciones

Establecer automáticamente durante [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CComApartment::CComApartment

El constructor.

```
CComApartment();
```

### <a name="remarks"></a>Observaciones

Inicializa los `CComApartment` miembros de datos [m_nLockCnt](#m_nlockcnt) y [m_hThread](#m_hthread).

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CComApartment::GetLockCount

Devuelve el recuento de bloqueos actual del subproceso.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Valor devuelto

El bloqueo cuenta en el subproceso.

## <a name="ccomapartmentlock"></a><a name="lock"></a>CComApartment::Bloqueo

Incrementa el recuento de bloqueos del subproceso.

```
LONG Lock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Llamado por [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

El recuento de bloqueos en el subproceso se utiliza con fines estadísticos.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CComApartment::m_dwThreadID

Contiene el identificador del subproceso.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CComApartment::m_hThread

Contiene el identificador del subproceso.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CComApartment::m_nLockCnt

Contiene el recuento de bloqueos actual del subproceso.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CComApartment::Desbloquear

Disminuye el recuento de bloqueos del subproceso.

```
LONG Unlock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Llamado por [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

El recuento de bloqueos en el subproceso se utiliza con fines estadísticos.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
