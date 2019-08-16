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
ms.openlocfilehash: f1941bfcd7689ab9d22f5094af0eb833a84dab6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497683"
---
# <a name="cautorevertimpersonation-class"></a>Clase CAutoRevertImpersonation

Esta clase revierte los objetos [CAccessToken](../../atl/reference/caccesstoken-class.md) a un estado de no suplantación cuando sale del ámbito.

## <a name="syntax"></a>Sintaxis

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construye un `CAutoRevertImpersonation` objeto.|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Destruye el objeto y revierte la suplantación del token de acceso.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatiza la reversión de suplantación de un token de acceso.|
|[CAutoRevertImpersonation::Detach](#detach)|Cancela la reversión de suplantación automática.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Recupera el token de acceso actual asociado a este objeto.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows NT o Windows 2000. Estos tokens de acceso se pueden representar con `CAccessToken` la clase.

A veces es necesario suplantar los tokens de acceso. Esta clase se proporciona por comodidad, pero no realiza la suplantación de los tokens de acceso; solo realiza la conversión automática a un estado no suplantado. Esto se debe a que la suplantación de acceso a tokens se puede realizar de varias maneras diferentes.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="attach"></a>CAutoRevertImpersonation:: Attach

Automatiza la reversión de suplantación de un token de acceso.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*pAT*<br/>
Dirección del objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) que se va a revertir automáticamente.

### <a name="remarks"></a>Comentarios

Este método solo se debe usar si el objeto [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se creó con un puntero `CAccessToken` nulo, o si se llamó previamente a [detach](#detach) . En casos sencillos, no es necesario utilizar este método.

##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Construye un objeto `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*pAT*<br/>
Dirección del objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) que se va a revertir automáticamente.

### <a name="remarks"></a>Comentarios

La suplantación real del token de acceso se debe realizar de forma independiente de y preferiblemente antes de la creación `CAutoRevertImpersonation` de un objeto. Esta suplantación se revierte automáticamente cuando el `CAutoRevertImpersonation` objeto sale del ámbito.

##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

Destruye el objeto y revierte la suplantación del token de acceso.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Comentarios

Revierte cualquier suplantación vigente actualmente para el objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) proporcionado en la construcción o a través del método [Attach](#attach) . Si no `CAccessToken` hay ningún objeto asociado, el destructor no tiene ningún efecto.

##  <a name="detach"></a>CAutoRevertImpersonation::D Etach

Cancela la reversión de suplantación automática.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md)asociada previamente, o null si no existe ninguna asociación.

### <a name="remarks"></a>Comentarios

La llamada a detach `CAutoRevertImpersonation` evita que el objeto revierta la suplantación vigente actualmente para el objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) asociado a este objeto. `CAutoRevertImpersonation`a continuación, se puede destruir sin ningún efecto o volver a asociar al `CAccessToken` mismo u otro objeto mediante [Attach](#attach).

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

Recupera el token de acceso actual asociado a este objeto.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md)asociada previamente, o null si no existe ninguna asociación.

### <a name="remarks"></a>Comentarios

Si se llama a este método para los fines que incluyen la reversión de una suplantación del `CAccessToken` objeto, se debe usar en su lugar el método [detach](#detach) .

## <a name="see-also"></a>Vea también

[Ejemplo de ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokens de acceso](/windows/win32/SecAuthZ/access-tokens)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
