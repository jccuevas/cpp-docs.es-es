---
title: Clase CComCritSecLock
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 24d141c5b0ec703feadcd7db96da33f9de940dda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327951"
---
# <a name="ccomcritseclock-class"></a>Clase CComCritSecLock

Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parámetros

*TLock*<br/>
El objeto que se va a bloquear y desbloquear.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|El constructor.|
|[CComCritSecLock::-CComCritSecLock](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Llame a este método para bloquear el objeto de sección crítica.|
|[CComCritSecLock::Unlock](#unlock)|Llame a este método para desbloquear el objeto de sección crítica.|

## <a name="remarks"></a>Observaciones

Utilice esta clase para bloquear y desbloquear objetos de una manera más segura que con la [clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) o [la clase CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

El constructor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
El objeto de sección crítica.

*bInitialLock*<br/>
El estado de bloqueo inicial: **true** significa bloqueado.

### <a name="remarks"></a>Observaciones

Inicializa el objeto de sección crítica.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock::-CComCritSecLock

Destructor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Observaciones

Desbloquea el objeto de sección crítica.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock::Lock

Llame a este método para bloquear el objeto de sección crítica.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si el objeto se ha bloqueado correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Si el objeto ya está bloqueado, se producirá un error ASSERT en las compilaciones de depuración.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock::Unlock

Llame a este método para desbloquear el objeto de sección crítica.

```
void Unlock() throw();
```

### <a name="remarks"></a>Observaciones

Si el objeto ya está desbloqueado, se producirá un error ASSERT en las compilaciones de depuración.

## <a name="see-also"></a>Consulte también

[Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Clase CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)
