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
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327965"
---
# <a name="ccomcriticalsection-class"></a>Clase CComCriticalSection

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítico.|
|[CComCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|
|[CComCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|
|[CComCriticalSection::Unlock](#unlock)|Libera la propiedad del objeto de sección crítica.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Un objeto CRITICAL_SECTION.|

## <a name="remarks"></a>Observaciones

`CComCriticalSection`es similar a la clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), excepto que debe inicializar y liberar explícitamente la sección crítica.

Normalmente, se `CComCriticalSection` usa a través del nombre **typedef** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Este nombre `CComCriticalSection` hace referencia cuando se usa [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Consulte [CComCritSecLock (clase)](../../atl/reference/ccomcritseclock-class.md) para obtener una `Lock` `Unlock` forma más segura de usar esta clase que llamar y directamente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

El constructor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Observaciones

Establece el [m_sec](#m_sec) miembro de datos en NULL.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSection::Init

Llama a la función [Win32 InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), que inicializa el objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito, E_OUTOFMEMORY o E_FAIL en caso de error.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CComCriticalSection::Lock

Llama a la función [De32 EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), que espera hasta que el subproceso puede tomar la propiedad del objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito, E_OUTOFMEMORY o E_FAIL en caso de error.

### <a name="remarks"></a>Observaciones

El objeto de sección crítica debe inicializarse primero con una llamada a la [Init](#init) método. Cuando el código protegido ha terminado de ejecutarse, el subproceso debe llamar a [Unlock](#unlock) para liberar la propiedad de la sección crítica.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSection::m_sec

Contiene un objeto de sección `CComCriticalSection` crítico que se utiliza en todos los métodos.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CComCriticalSection::Term

Llama a la función [Win32 DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), que libera todos los recursos utilizados por el objeto de sección crítica contenido en el miembro de datos [m_sec.](#m_sec)

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Una `Term` vez que se ha llamado, la sección crítica ya no se puede utilizar para la sincronización.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CComCriticalSection::Unlock

Llama a la función [Win32 LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), que libera la propiedad del objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para obtener primero la propiedad, el subproceso debe llamar a la [Lock](#lock) método. Cada llamada `Lock` requiere una llamada `Unlock` correspondiente para liberar la propiedad de la sección crítica.

## <a name="see-also"></a>Consulte también

[Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
