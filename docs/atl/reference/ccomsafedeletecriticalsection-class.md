---
title: Clase CComSafeDeleteCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327363"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Clase CComSafeDeleteCriticalSection

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CcomSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|El constructor.|
|[CComSafeDeleteCriticalSection::-CComSafeDeleteCriticalSection](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítico.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|
|[CComSafeDeleteCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Indica si `CRITICAL_SECTION` se ha inicializado el objeto interno.|

## <a name="remarks"></a>Observaciones

`CComSafeDeleteCriticalSection`deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin `CComSafeDeleteCriticalSection` embargo, proporciona mecanismos de seguridad adicionales a través de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Cuando una `CComSafeDeleteCriticalSection` instancia de sale del ámbito o se elimina explícitamente de la memoria, el objeto de sección crítica subyacente se limpiará automáticamente si sigue siendo válido. Además, el [CComSafeDeleteCriticalSection::Term](#term) método se cerrará correctamente si el objeto de sección crítica subyacente aún no se ha asignado o ya se ha liberado de la memoria.

Consulte [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases auxiliares de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CcomSafeDeleteCriticalSection

El constructor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Observaciones

Establece el [m_bInitialized](#m_binitialized) miembro de datos en FALSE.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafeDeleteCriticalSection::-CComSafeDeleteCriticalSection

Destructor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Observaciones

Libera el `CRITICAL_SECTION` objeto interno de la memoria si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en TRUE.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteCriticalSection::Init

Llama a la implementación de la clase base de [Init](/visualstudio/debugger/init) y establece [m_bInitialized](#m_binitialized) en TRUE si se realiza correctamente.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteCriticalSection::Lock

Llama a la implementación de la clase base de [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Observaciones

Este método supone que el [m_bInitialized](#m_binitialized) miembro de datos se establece en TRUE al entrar. Se genera una aserción en compilaciones de depuración si no se cumple esta condición.

Para obtener más información sobre el comportamiento de la función, consulte [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized

Indica si `CRITICAL_SECTION` se ha inicializado el objeto interno.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Observaciones

El `m_bInitialized` miembro de datos se utiliza para `CRITICAL_SECTION` realizar un seguimiento de la validez del objeto subyacente asociado a la [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) clase. El objeto `CRITICAL_SECTION` subyacente no se intentará liberar de la memoria si esta marca no está establecida en TRUE.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteCriticalSection::Term

Llama a la implementación de la clase base `CRITICAL_SECTION` de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) si el objeto interno es válido.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)o S_OK si [m_bInitialized](#m_binitialized) se estableció en FALSE en la entrada.

### <a name="remarks"></a>Observaciones

Es seguro llamar a este método `CRITICAL_SECTION` incluso si el objeto interno no es válido. El destructor de esta clase llama a este método si el miembro de datos [m_bInitialized](#m_binitialized) se establece en TRUE.

## <a name="see-also"></a>Consulte también

[Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
