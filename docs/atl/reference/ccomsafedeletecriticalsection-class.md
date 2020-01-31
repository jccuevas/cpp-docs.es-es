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
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821654"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Clase CComSafeDeleteCriticalSection

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|El constructor.|
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|
|[CComSafeDeleteCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Marca si se ha inicializado el objeto de `CRITICAL_SECTION` interno.|

## <a name="remarks"></a>Notas

`CComSafeDeleteCriticalSection` deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComSafeDeleteCriticalSection` proporciona mecanismos de seguridad adicionales en [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Cuando una instancia de `CComSafeDeleteCriticalSection` sale del ámbito o se elimina explícitamente de la memoria, el objeto de sección crítica subyacente se limpiará automáticamente si sigue siendo válido. Además, el método [CComSafeDeleteCriticalSection:: Term](#term) se cerrará correctamente si aún no se ha asignado el objeto de sección crítica subyacente o si ya se ha liberado de la memoria.

Vea [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases auxiliares de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Requisitos de

**Encabezado:** atlcore. h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

El constructor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Notas

Establece el miembro de datos [m_bInitialized](#m_binitialized) en false.

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection

Destructor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Notas

Libera el objeto `CRITICAL_SECTION` interno de la memoria si el miembro de datos [m_bInitialized](#m_binitialized) está establecido en true.

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

Llama a la implementación de la clase base de [init](/visualstudio/debugger/init) y establece [m_bInitialized](#m_binitialized) en true si se realiza correctamente.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection:: init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Llama a la implementación de la clase base de [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Notas

Este método presupone que el miembro de datos [m_bInitialized](#m_binitialized) está establecido en true en la entrada. Se genera una aserción en las compilaciones de depuración si no se cumple esta condición.

Para obtener más información sobre el comportamiento de la función, consulte [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Marca si se ha inicializado el objeto de `CRITICAL_SECTION` interno.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Notas

El miembro de datos `m_bInitialized` se usa para realizar un seguimiento de la validez del objeto de `CRITICAL_SECTION` subyacente asociado a la clase [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) . No se intentará liberar el objeto de `CRITICAL_SECTION` subyacente de la memoria si esta marca no se establece en TRUE.

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

Llama a la implementación de la clase base de [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term) si el objeto de `CRITICAL_SECTION` interno es válido.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)o S_OK si [m_bInitialized](#m_binitialized) se estableció en false en la entrada.

### <a name="remarks"></a>Notas

Es seguro llamar a este método incluso si el objeto de `CRITICAL_SECTION` interno no es válido. El destructor de esta clase llama a este método si el miembro de datos [m_bInitialized](#m_binitialized) está establecido en true.

## <a name="see-also"></a>Vea también

[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
