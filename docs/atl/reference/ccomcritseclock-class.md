---
title: CComCritSecLock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab3c4b349b64b96b8aeb7a53d6bf8809f41cea7b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097788"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock (clase)

Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parámetros

*TLock*<br/>
Objeto que se va a ser bloqueadas y desbloqueadas.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|El constructor.|
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Llame a este método para bloquear el objeto de sección crítica.|
|[CComCritSecLock::Unlock](#unlock)|Llame a este método para desbloquear el objeto de sección crítica.|

## <a name="remarks"></a>Comentarios

Utilice esta clase para bloquear y desbloquear los objetos de un modo más seguro que con la [CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md) o [CComAutoCriticalSection (clase)](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

El constructor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parámetros

*CS*<br/>
El objeto de sección crítica.

*bInitialLock*<br/>
El estado de bloqueo inicial: **true** forma bloqueada.

### <a name="remarks"></a>Comentarios

Inicializa el objeto de sección crítica.

##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock

Destructor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Comentarios

Desbloquea el objeto de sección crítica.

##  <a name="lock"></a>  CComCritSecLock::Lock

Llame a este método para bloquear el objeto de sección crítica.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si el objeto ha bloqueado correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Si el objeto ya está bloqueado, se producirá un error de aserción en las compilaciones de depuración.

##  <a name="unlock"></a>  CComCritSecLock::Unlock

Llame a este método para desbloquear el objeto de sección crítica.

```
void Unlock() throw();
```

### <a name="remarks"></a>Comentarios

Si el objeto ya está desbloqueado, se producirá un error de aserción en las compilaciones de depuración.

## <a name="see-also"></a>Vea también

[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection (clase)](../../atl/reference/ccomautocriticalsection-class.md)
