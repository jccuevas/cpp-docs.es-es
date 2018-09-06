---
title: CComSafeDeleteCriticalSection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ea024475f824745ac8f99a957b5a75f9f4db22c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754803"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection (clase)

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
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|
|[CComSafeDeleteCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Marcas si interno `CRITICAL_SECTION` objeto se ha inicializado.|

## <a name="remarks"></a>Comentarios

`CComSafeDeleteCriticalSection` se deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComSafeDeleteCriticalSection` proporciona mecanismos de seguridad adicionales a través de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Cuando una instancia de `CComSafeDeleteCriticalSection` sale del ámbito o no está explícitamente se elimina de la memoria, el objeto de sección crítica subyacente automáticamente se limpiará si aún es válido. Además, el [CComSafeDeleteCriticalSection::Term](#term) método se cerrará correctamente si el objeto de sección crítica subyacente no se ha asignado o ya se ha liberado de memoria.

Consulte [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases auxiliares de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

El constructor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Comentarios

Establece el [m_bInitialized](#m_binitialized) miembro de datos en FALSE.

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection

Destructor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Comentarios

Libera interno `CRITICAL_SECTION` objeto de la memoria si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en TRUE.

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

Llama a la implementación de clase base [Init](/visualstudio/debugger/init) y establece [m_bInitialized](#m_binitialized) en TRUE si se realiza correctamente.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Llama a la implementación de clase base [bloqueo](ccomcriticalsection-class.md#lock).  

```
HRESULT Lock();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Comentarios

Este método supone que la [m_bInitialized](#m_binitialized) miembro de datos está establecido en TRUE en la entrada. Si no se cumple esta condición, se genera una aserción en las compilaciones de depuración.

Para obtener más información sobre el comportamiento de la función, consulte [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Marcas si interno `CRITICAL_SECTION` objeto se ha inicializado.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Comentarios

El `m_bInitialized` miembro de datos se usa para realizar un seguimiento de la validez de subyacente `CRITICAL_SECTION` objeto asociado con el [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) clase. Subyacente `CRITICAL_SECTION` objeto no se volverá a intentar para liberarse de la memoria si esta marca no se establece en TRUE.

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

Llama a la implementación de clase base [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) si interno `CRITICAL_SECTION` objeto es válido.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), o S_OK si [m_bInitialized](#m_binitialized) se estableció en FALSE después de la entrada.

### <a name="remarks"></a>Comentarios

Es seguro llamar a este aunque método interno `CRITICAL_SECTION` objeto no es válido. El destructor de esta clase llama a este método si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en TRUE.

## <a name="see-also"></a>Vea también

[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
