---
title: Clase CDacl
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: a37ef47a4ea89d9ec24fac417e5b715bd2602fd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496928"
---
# <a name="cdacl-class"></a>Clase CDacl

Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CDacl : public CAcl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|El constructor.|
|[CDacl::~CDacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Agrega una ACE (entrada de control de acceso) permitida `CDacl` al objeto.|
|[CDacl::AddDeniedAce](#adddeniedace)|Agrega una ACE denegada `CDacl` al objeto.|
|[CDacl::GetAceCount](#getacecount)|Devuelve el número de ACE (entradas de control de acceso) en `CDacl` el objeto.|
|[CDacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) del `CDacl` objeto.|
|[CDacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas en `CDacl` el objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

El descriptor de seguridad de un objeto puede contener una DACL. Una DACL contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden tener acceso al objeto. Si una DACL está vacía (es decir, contiene cero ACE), no se concede ningún acceso explícitamente, por lo que el acceso se deniega implícitamente. Sin embargo, si el descriptor de seguridad de un objeto no tiene una DACL, el objeto no está protegido y todos los usuarios tienen acceso completo.

Para recuperar la DACL de un objeto, debe ser el propietario del objeto o tener acceso de READ_CONTROL al objeto. Para cambiar la DACL de un objeto, debe tener el acceso de WRITE_DAC al objeto.

Utilice los métodos de clase proporcionados para crear, agregar, quitar y eliminar ACE del `CDacl` objeto. Vea también [AtlGetDacl](security-global-functions.md#atlgetdacl) y [AtlSetDacl](security-global-functions.md#atlsetdacl).

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Agrega una ACE (entrada de control de acceso) permitida `CDacl` al objeto.

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto [CSid](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que se va a permitir `CSid` para el objeto especificado.

*AceFlags*<br/>
Un conjunto de marcadores de bits que controlan la herencia de ACE.

*pObjectType*<br/>
Tipo del objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la ACE se agrega al `CDacl` objeto, false en caso de error.

### <a name="remarks"></a>Comentarios

Un `CDacl` objeto contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que permite el `CDacl` acceso al objeto.

Vea [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una descripción de las distintas marcas que se pueden establecer en `AceFlags` el parámetro.

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

Agrega una ACE denegada (entrada de control de acceso `CDacl` ) al objeto.

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto `CSid`.

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que se va a denegar para el objeto especificado `CSid` .

*AceFlags*<br/>
Un conjunto de marcadores de bits que controlan la herencia de ACE. El valor predeterminado es 0 en el primer formulario del método.

*pObjectType*<br/>
Tipo del objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la ACE se agrega al `CDacl` objeto, false en caso de error.

### <a name="remarks"></a>Comentarios

Un `CDacl` objeto contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que deniega el `CDacl` acceso al objeto.

Vea [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una descripción de las distintas marcas que se pueden establecer en `AceFlags` el parámetro.

##  <a name="cdacl"></a>  CDacl::CDacl

El constructor.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Una estructura `ACL` existente (lista de control de acceso).

### <a name="remarks"></a>Comentarios

El `CDacl` objeto se puede crear opcionalmente con una estructura `ACL` existente. Es importante tener en cuenta que solo se debe pasar como este parámetro una DACL (lista de control de acceso discrecional) y no una SACL (lista de control de acceso del sistema). En las compilaciones de depuración, pasar una SACL producirá una ASERCIÓN. En las compilaciones de versión, el paso de una SACL hará que se omitan las ACE (entradas de control de acceso) en la ACL y no se producirá ningún error.

##  <a name="dtor"></a>  CDacl::~CDacl

Destructor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos adquiridos por el objeto, incluidas todas las ACE (entradas de control de acceso) mediante [CDacl:: RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>  CDacl::GetAceCount

Devuelve el número de ACE (entradas de control de acceso) en `CDacl` el objeto.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ACE contenidas `CDacl` en el objeto.

##  <a name="operator_eq"></a>CDacl:: Operator =

Operador de asignación.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
ACL (lista de control de acceso) que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actualizado `CDacl` .

### <a name="remarks"></a>Comentarios

Debe asegurarse de que solo pasa una DACL (lista de control de acceso discrecional) a esta función. Pasar una SACL (lista de control de acceso del sistema) a esta función producirá una ASERCIÓN en las compilaciones de depuración, pero no producirá ningún error en las compilaciones de versión.

##  <a name="removeace"></a>  CDacl::RemoveAce

Quita una ACE específica (entrada de control de acceso) del `CDacl` objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE que se va a quitar.

### <a name="remarks"></a>Comentarios

Este método se deriva de [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

Quita todas las ACE (entradas de control de acceso) contenidas `CDacl` en el objeto.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Comentarios

Quita todas `ACE` las estructuras (entradas de control de acceso) (si existen) `CDacl` en el objeto.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[CAcl (clase)](../../atl/reference/cacl-class.md)<br/>
[Unas](/windows/win32/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
