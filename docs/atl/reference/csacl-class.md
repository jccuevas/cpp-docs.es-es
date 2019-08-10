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
ms.openlocfilehash: b75dc4110b785f0ab1f55ba5c31df7d3fc6fbd37
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915754"
---
# <a name="csacl-class"></a>Clase CSacl

Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSacl : public CAcl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|El constructor.|
|[CSacl::~CSacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Agrega una entrada de control de acceso (ACE) de auditoría `CSacl` al objeto.|
|[CSacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de acceso (ACE) en `CSacl` el objeto.|
|[CSacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) del `CSacl` objeto.|
|[CSacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas en `CSacl` el objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSacl:: Operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Una SACL contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad de un controlador de dominio. Tenga en cuenta que una SACL solo genera entradas de registro en el controlador de dominio en el que se produjo el intento de acceso, no en todos los controladores de dominio que contengan una réplica del objeto.

Para establecer o recuperar la SACL en el descriptor de seguridad de un objeto, el privilegio SE_SECURITY_NAME debe estar habilitado en el token de acceso del subproceso que lo solicita. El grupo administradores tiene este privilegio concedido de forma predeterminada y se puede conceder a otros usuarios o grupos. Tener el privilegio concedido no es todo lo necesario: antes de que se pueda realizar la operación definida por el privilegio, el privilegio debe estar habilitado en el token de acceso de seguridad para que surta efecto. El modelo permite que los privilegios se habiliten solo para operaciones específicas del sistema y, después, se deshabiliten cuando ya no se necesiten. Vea [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl) para obtener ejemplos de cómo habilitar SE_SECURITY_NAME.

Utilice los métodos de clase proporcionados para agregar, quitar, crear y eliminar ACE del `SACL` objeto. Vea también [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl).

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/desktop/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="addauditace"></a>  CSacl::AddAuditAce

Agrega una entrada de control de acceso (ACE) de auditoría `CSacl` al objeto.

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
Objeto [CSid](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que se va a auditar `CSid` para el objeto especificado.

*bSuccess*<br/>
Especifica si se van a auditar los intentos de acceso permitidos. Establezca esta marca en true para habilitar la auditoría; en caso contrario, establézcalo en false.

*bFailure*<br/>
Especifica si se van a auditar los intentos de acceso denegados. Establezca esta marca en true para habilitar la auditoría; en caso contrario, establézcalo en false.

*AceFlags*<br/>
Un conjunto de marcadores de bits que controlan la herencia de ACE.

*pObjectType*<br/>
Tipo del objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la ACE se agrega al `CSacl` objeto, false en caso de error.

### <a name="remarks"></a>Comentarios

Un `CSacl` objeto contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad. Este método agrega esta ACE al `CSacl` objeto.

Consulte [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) para obtener una descripción de las distintas marcas que se pueden establecer en el parámetro *AceFlags* .

##  <a name="csacl"></a>  CSacl::CSacl

El constructor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Una estructura `ACL` existente (lista de control de acceso).

### <a name="remarks"></a>Comentarios

El `CSacl` objeto se puede crear opcionalmente con una estructura `ACL` existente. Asegúrese de que este parámetro es una lista de control de acceso del sistema (SACL) y no una lista de control de acceso discrecional (DACL). En las compilaciones de depuración, si se proporciona una DACL, se producirá una aserción. En las compilaciones de versión, se omiten las entradas de una DACL.

##  <a name="dtor"></a>  CSacl::~CSacl

Destructor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso (ACE).

##  <a name="getacecount"></a>  CSacl::GetAceCount

Devuelve el número de entradas de control de acceso (ACE) en `CSacl` el objeto.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ACE contenidas `CSacl` en el objeto.

##  <a name="operator_eq"></a>CSacl:: Operator =

Operador de asignación.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`ACL` (Lista de control de acceso) que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actualizado `CSacl` . Asegúrese de que `ACL` el parámetro es realmente una lista de control de acceso de sistema (SACL) y no una lista de control de acceso discrecional (DACL). En la depuración, se producirá una aserción y, en `ACL` las compilaciones de versión, se omitirá el parámetro.

##  <a name="removeace"></a>  CSacl::RemoveAce

Quita una ACE específica (entrada de control de acceso) del `CSacl` objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE que se va a quitar.

### <a name="remarks"></a>Comentarios

Este método se deriva de [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

Quita todas las entradas de control de acceso (ACE) contenidas `CSacl` en el objeto.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Comentarios

Quita todas `ACE` las `CSacl` estructuras (si existen) del objeto.

## <a name="see-also"></a>Vea también

[CAcl (clase)](../../atl/reference/cacl-class.md)<br/>
[Unas](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
