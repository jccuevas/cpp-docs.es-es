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
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327153"
---
# <a name="cdacl-class"></a>Clase CDacl

Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CDacl : public CAcl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|El constructor.|
|[CDacl::-CDacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Agrega una ACE permitida (entrada de `CDacl` control de acceso) al objeto.|
|[CDacl::AddDeniedAce](#adddeniedace)|Agrega una ACE denegada `CDacl` al objeto.|
|[CDacl::GetAceCount](#getacecount)|Devuelve el número de ACE (entradas de `CDacl` control de acceso) en el objeto.|
|[CDacl::RemoveAce](#removeace)|Quita un ACE específico (entrada de `CDacl` control de acceso) del objeto.|
|[CDacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas `CDacl` en el objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDacl::operador ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

El descriptor de seguridad de un objeto puede contener una DACL. Una DACL contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden acceder al objeto. Si una DACL está vacía (es decir, contiene cero ACE), no se concede explícitamente ningún acceso, por lo que el acceso se deniega implícitamente. Sin embargo, si el descriptor de seguridad de un objeto no tiene una DACL, el objeto está desprotegido y todos tienen acceso completo.

Para recuperar la DACL de un objeto, debe ser el propietario del objeto o tener acceso READ_CONTROL al objeto. Para cambiar la DACL de un objeto, debe tener WRITE_DAC acceso al objeto.

Utilice los métodos de clase proporcionados para crear, `CDacl` agregar, quitar y eliminar ACE del objeto. Vea también [AtlGetDacl](security-global-functions.md#atlgetdacl) y [AtlSetDacl](security-global-functions.md#atlsetdacl).

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cacl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce

Agrega una ACE permitida (entrada de `CDacl` control de acceso) al objeto.

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
Un [CSid](../../atl/reference/csid-class.md) objeto.

*AccessMask*<br/>
Especifica la máscara de derechos de acceso `CSid` que se permitirá para el objeto especificado.

*AceFlags*<br/>
Conjunto de indicadores de bits que controlan la herencia de ACE.

*pObjectType*<br/>
El tipo de objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ACE `CDacl` se agrega al objeto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Un `CDacl` objeto contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que `CDacl` permite el acceso al objeto.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una descripción de `AceFlags` los distintos indicadores que se pueden establecer en el parámetro.

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce

Agrega un ACE denegado (entrada de `CDacl` control de acceso) al objeto.

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
Objeto `CSid` .

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que `CSid` se deniegan para el objeto especificado.

*AceFlags*<br/>
Conjunto de indicadores de bits que controlan la herencia de ACE. El valor predeterminado es 0 en la primera forma del método.

*pObjectType*<br/>
El tipo de objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ACE `CDacl` se agrega al objeto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Un `CDacl` objeto contiene cero o más ACE (entradas de control de acceso) que identifican a los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que deniega el `CDacl` acceso al objeto.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una descripción de `AceFlags` los distintos indicadores que se pueden establecer en el parámetro.

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl

El constructor.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Una `ACL` estructura existente (lista de control de acceso).

### <a name="remarks"></a>Observaciones

El `CDacl` objeto se puede crear `ACL` opcionalmente utilizando una estructura existente. Es importante tener en cuenta que sólo una DACL (lista de control de acceso discrecional) y no una SACL (lista de control de acceso del sistema), debe pasarse como este parámetro. En las compilaciones de depuración, pasar una SACL provocará un ASSERT. En las compilaciones de la versión, pasar una SACL hará que las ACE (entradas de control de acceso) en el ACL sean ignoradas, y no ocurrirá ningún error.

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl::-CDacl

Destructor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos adquiridos por el objeto, incluidas todas las ACE (entradas de control de acceso) mediante [CDacl::RemoveAllAces](#removeallaces).

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount

Devuelve el número de ACE (entradas de `CDacl` control de acceso) en el objeto.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ACE `CDacl` contenidas en el objeto.

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::operador ?

Operador de asignación.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
ACL (lista de control de acceso) que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CDacl` al objeto actualizado.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que solo pasa una DACL (lista de control de acceso discrecional) a esta función. Pasar una SACL (lista de control de acceso del sistema) a esta función provocará un ASSERT en compilaciones de depuración, pero no provocará ningún error en las compilaciones de versión.

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce

Quita un ACE específico (entrada de `CDacl` control de acceso) del objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice a la entrada ACE que se va a quitar.

### <a name="remarks"></a>Observaciones

Este método se deriva de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::RemoveAllAces

Quita todas las ACE (entradas de control de acceso) contenidas en el `CDacl` objeto.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Observaciones

Quita todas `ACE` las estructuras (entrada de control `CDacl` de acceso) (si las hay) del objeto.

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[Clase CAcl](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Ases](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
