---
title: Clase CComCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: ee4ce32ed4ae04bc3b390af5cf104b8a0af599f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497278"
---
# <a name="ccomcriticalsection-class"></a>Clase CComCriticalSection

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|
|[CComCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|
|[CComCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|
|[CComCriticalSection::Unlock](#unlock)|Libera la propiedad del objeto de sección crítica.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Objeto CRITICAL_SECTION.|

## <a name="remarks"></a>Comentarios

`CComCriticalSection`es similar a la clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), salvo que debe inicializar y liberar explícitamente la sección crítica.

Normalmente, se usa `CComCriticalSection` a través del nombre de **typedef** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Este nombre hace `CComCriticalSection` referencia al uso de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Vea la [clase CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) para obtener una manera más segura de usar esta `Lock` clase `Unlock` que llamar a e directamente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore. h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

El constructor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Comentarios

Establece el miembro de datos [m_sec](#m_sec) en NULL.

##  <a name="init"></a>  CComCriticalSection::Init

Llama a la función [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)de Win32, que inicializa el objeto de sección crítica incluido en el miembro de datos [m_sec](#m_sec) .

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente, E_OUTOFMEMORY o E_FAIL en caso de error.

##  <a name="lock"></a>  CComCriticalSection::Lock

Llama a la función [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)de Win32, que espera hasta que el subproceso pueda asumir la propiedad del objeto de sección crítica incluido en el miembro de datos [m_sec](#m_sec) .

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente, E_OUTOFMEMORY o E_FAIL en caso de error.

### <a name="remarks"></a>Comentarios

El objeto de sección crítica primero se debe inicializar con una llamada al método [init](#init) . Cuando el código protegido ha terminado de ejecutarse, el subproceso debe llamar a [Unlock](#unlock) para liberar la propiedad de la sección crítica.

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

Contiene un objeto de sección crítica que usan todos `CComCriticalSection` los métodos.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

Llama a la función [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)de Win32, que libera todos los recursos utilizados por el objeto de sección crítica incluido en el miembro de datos [m_sec](#m_sec) .

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Una `Term` vez que se ha llamado a, la sección crítica ya no se puede usar para la sincronización.

##  <a name="unlock"></a>  CComCriticalSection::Unlock

Llama a la función [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)de Win32, que libera la propiedad del objeto de sección crítica incluido en el miembro de datos [m_sec](#m_sec) .

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para obtener primero la propiedad, el subproceso debe llamar al método [Lock](#lock) . Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.

## <a name="see-also"></a>Vea también

[CComFakeCriticalSection (clase)](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock (clase)](../../atl/reference/ccomcritseclock-class.md)
