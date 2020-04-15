---
title: Clase CAutoRevertImpersonation
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 813b6f0dd33bdfa85476b816086217a7892f4476
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318790"
---
# <a name="cautorevertimpersonation-class"></a>Clase CAutoRevertImpersonation

Esta clase revierte [CAccessToken](../../atl/reference/caccesstoken-class.md) objetos a un estado nonimpersonaque cuando sale del ámbito.

## <a name="syntax"></a>Sintaxis

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construye un `CAutoRevertImpersonation` objeto|
|[CAutoRevertImpersonation::-CAutoRevertImpersonation](#dtor)|Destruye el objeto y revierte la suplantación de token de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatiza la reversión de suplantación de un token de acceso.|
|[CAutoRevertImpersonation::Detach](#detach)|Cancela la reversión de suplantación automática.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Recupera la corriente del token de acceso asociada a este objeto.|

## <a name="remarks"></a>Observaciones

Un token de [acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows NT o Windows 2000. Estos tokens de acceso se `CAccessToken` pueden representar con la clase.

A veces es necesario suplantar tokens de acceso. Esta clase se proporciona como una conveniencia, pero no realiza la suplantación de tokens de acceso; sólo realiza la reversión automática a un estado nonimpersona. Esto se debe a que la suplantación de acceso a tokens se puede realizar de varias maneras diferentes.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>CAutoRevertImpersonation::Attach

Automatiza la reversión de suplantación de un token de acceso.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*palmadita*<br/>
La dirección del objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) que se revertirá automáticamente

### <a name="remarks"></a>Observaciones

Este método solo se debe usar si el [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objeto se creó con un NULL `CAccessToken` puntero, o si Se llamó a [Detach](#detach) anteriormente. Para casos simples, no es necesario utilizar este método.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Construye un objeto `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*palmadita*<br/>
La dirección del objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) que se revertirá automáticamente.

### <a name="remarks"></a>Observaciones

La suplantación real del token de acceso debe realizarse por `CAutoRevertImpersonation` separado y preferiblemente antes de la creación de un objeto. Esta suplantación se revertirá `CAutoRevertImpersonation` automáticamente cuando el objeto salga del ámbito.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>CAutoRevertImpersonation::-CAutoRevertImpersonation

Destruye el objeto y revierte la suplantación de token de acceso.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Observaciones

Revierte cualquier suplantación actualmente en vigor para el [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto proporcionado en la construcción o a través de la [Attach](#attach) método. Si `CAccessToken` no está asociado, el destructor no tiene ningún efecto.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>CAutoRevertImpersonation::Detach

Cancela la reversión de suplantación automática.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección del [CAccessToken](../../atl/reference/caccesstoken-class.md)asociado anteriormente , o NULL si no existía ninguna asociación.

### <a name="remarks"></a>Observaciones

Llamar a **Detach** impide que el `CAutoRevertImpersonation` objeto revierta cualquier suplantación actualmente en vigor para el [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto asociado a este objeto. `CAutoRevertImpersonation`puede ser destruido sin ningún efecto o reasociado al mismo u otro `CAccessToken` objeto usando [Adjuntar](#attach).

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Recupera la corriente del token de acceso asociada a este objeto.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección del [CAccessToken](../../atl/reference/caccesstoken-class.md)asociado anteriormente , o NULL si no existía ninguna asociación.

### <a name="remarks"></a>Observaciones

Si se llama a este método para los fines que incluyen `CAccessToken` la reversión de una suplantación del objeto, el [Detach](#detach) método debe utilizarse en su lugar.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokens de acceso](/windows/win32/SecAuthZ/access-tokens)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
