---
title: Clase CSacl
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: d5a060555901361ef6c70c6a4f801605eafd92cf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746553"
---
# <a name="csacl-class"></a>Clase CSacl

Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSacl : public CAcl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|El constructor.|
|[CSacl::-CSacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Agrega una entrada de control de acceso `CSacl` de auditoría (ACE) al objeto.|
|[CSacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de `CSacl` acceso (ACE) en el objeto.|
|[CSacl::RemoveAce](#removeace)|Quita un ACE específico (entrada de `CSacl` control de acceso) del objeto.|
|[CSacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas `CSacl` en el objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSacl::operador ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

Una SACL contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad de un controlador de dominio. Tenga en cuenta que una SACL genera entradas de registro solo en el controlador de dominio donde se produjo el intento de acceso, no en todos los controladores de dominio que contienen una réplica del objeto.

Para establecer o recuperar la SACL en el descriptor de seguridad de un objeto, el privilegio SE_SECURITY_NAME debe estar habilitado en el token de acceso del subproceso solicitante. El grupo de administradores tiene este privilegio concedido de forma predeterminada y se puede conceder a otros usuarios o grupos. Tener el privilegio concedido no es todo lo que se requiere: antes de que se pueda realizar la operación definida por el privilegio, el privilegio debe estar habilitado en el token de acceso de seguridad para que surta efecto. El modelo permite habilitar privilegios solo para operaciones específicas del sistema y, a continuación, deshabilitarlos cuando ya no son necesarios. Consulte [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl) para obtener ejemplos de cómo habilitar SE_SECURITY_NAME.

Utilice los métodos de clase proporcionados para agregar, `SACL` quitar, crear y eliminar ACE del objeto. Vea también [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl).

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cacl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce

Agrega una entrada de control de acceso `CSacl` de auditoría (ACE) al objeto.

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
El [cSid](../../atl/reference/csid-class.md) objeto.

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que `CSid` se va a auditar para el objeto especificado.

*bSuccess*<br/>
Especifica si se deben auditar los intentos de acceso permitidos. Establezca esta marca en true para habilitar la auditoría; de lo contrario, establézcalo en false.

*bFailure*<br/>
Especifica si se deben auditar los intentos de acceso denegado. Establezca esta marca en true para habilitar la auditoría; de lo contrario, establézcalo en false.

*AceFlags*<br/>
Conjunto de indicadores de bits que controlan la herencia de ACE.

*pObjectType*<br/>
El tipo de objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ACE `CSacl` se agrega al objeto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Un `CSacl` objeto contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad. Este método agrega dicha ACE `CSacl` al objeto.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una descripción de los distintos indicadores que se pueden establecer en el parámetro *AceFlags.*

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl

El constructor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Una `ACL` estructura existente (lista de control de acceso).

### <a name="remarks"></a>Observaciones

El `CSacl` objeto se puede crear `ACL` opcionalmente utilizando una estructura existente. Asegúrese de que este parámetro sea una lista de control de acceso del sistema (SACL) y no una lista de control de acceso discrecional (DACL). En compilaciones de depuración, si se proporciona una DACL se producirá una aserción. En las compilaciones de versiones se omiten todas las entradas de una DACL.

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl::-CSacl

Destructor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso (ACE).

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount

Devuelve el número de entradas de control de `CSacl` acceso (ACE) en el objeto.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ACE `CSacl` contenidas en el objeto.

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::operador ?

Operador de asignación.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `ACL` (lista de control de acceso) que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CSacl` al objeto actualizado. Asegúrese `ACL` de que el parámetro sea realmente una lista de control de acceso del sistema (SACL) y no una lista de control de acceso discrecional (DACL). En las compilaciones de depuración se producirá `ACL` una aserción y en las compilaciones de versión se omitirá el parámetro.

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::RemoveAce

Quita un ACE específico (entrada de `CSacl` control de acceso) del objeto.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice a la entrada ACE que se va a quitar.

### <a name="remarks"></a>Observaciones

Este método se deriva de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::RemoveAllAces

Quita todas las entradas de control de acceso (ACE) contenidas en el `CSacl` objeto.

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Observaciones

Quita todas `ACE` las estructuras (si las hay) del `CSacl` objeto.

## <a name="see-also"></a>Vea también

[Clase CAcl](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Ases](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
