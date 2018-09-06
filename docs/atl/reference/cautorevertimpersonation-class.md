---
title: CAutoRevertImpersonation (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f0615dc37070311428ec12894bcaeea8febe8d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760622"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation (clase)

Esta clase se revierte [CAccessToken](../../atl/reference/caccesstoken-class.md) objetos a un estado nonimpersonating cuando sale del ámbito.

## <a name="syntax"></a>Sintaxis

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construye un `CAutoRevertImpersonation` objeto|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Destruye el objeto y revierte la suplantación de token de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatiza la reversión de suplantación de un token de acceso.|
|[CAutoRevertImpersonation::Detach](#detach)|Cancela la reversión de la suplantación automática.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Recupera el actual token de acceso asociado a este objeto.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/desktop/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows NT o Windows 2000. Estos tokens de acceso se pueden representar con el `CAccessToken` clase.

A veces es necesario suplantar los tokens de acceso. Esta clase se proporciona por comodidad, pero no realiza la suplantación de tokens de acceso; solo se realiza la reversión automática a un estado nonimpersonated. Esto es porque la suplantación del token de acceso puede realizarse de varias maneras diferentes.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="attach"></a>  CAutoRevertImpersonation::Attach

Automatiza la reversión de suplantación de un token de acceso.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*PAT*  
La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto al que se revierten automáticamente

### <a name="remarks"></a>Comentarios

Este método solo debe usarse si la [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se creó el objeto con un valor NULL `CAccessToken` puntero, o si [Detach](#detach) se llamó anteriormente. Los casos sencillos, no es necesario usar este método.

##  <a name="cautorevertimpersonation"></a>  CAutoRevertImpersonation::CAutoRevertImpersonation

Construye un objeto `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parámetros

*PAT*  
La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto al que se revierten automáticamente.

### <a name="remarks"></a>Comentarios

La suplantación del token de acceso real debe realizarse por separado de y, preferiblemente, antes de la creación de un `CAutoRevertImpersonation` objeto. Esta suplantación, se revertirá automáticamente cuando el `CAutoRevertImpersonation` objeto queda fuera del ámbito.

##  <a name="dtor"></a>  CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

Destruye el objeto y revierte la suplantación de token de acceso.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Comentarios

Revierte ninguna suplantación actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto proporcionado en la construcción o a través del [adjuntar](#attach) método. Si no hay ningún `CAccessToken` está asociado, el destructor no tiene ningún efecto.

##  <a name="detach"></a>  CAutoRevertImpersonation::Detach

Cancela la reversión de la suplantación automática.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección del asociado anteriormente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.

### <a name="remarks"></a>Comentarios

Una llamada a **Detach** impide la `CAutoRevertImpersonation` objeto revertir cualquier suplantación actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto asociado a este objeto. `CAutoRevertImpersonation` a continuación, se destruye no tiene ningún efecto o vuelto a asociar a la misma u otra `CAccessToken` objeto [adjuntar](#attach).

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

Recupera el actual token de acceso asociado a este objeto.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valor devuelto

La dirección del asociado anteriormente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.

### <a name="remarks"></a>Comentarios

Si se llama a este método para los fines que incluyen la reversión de una suplantación de la `CAccessToken` objeto, el [Detach](#detach) método se debe utilizar en su lugar.

## <a name="see-also"></a>Vea también

[Ejemplo ATLSecurity](../../visual-cpp-samples.md)   
[Tokens de acceso](/windows/desktop/SecAuthZ/access-tokens)   
[Información general de clases](../../atl/atl-class-overview.md)
