---
title: CSacl (clase)
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
ms.openlocfilehash: f8820be3073c6ffaffdaa9d04a7338ad584d36ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278025"
---
# <a name="csacl-class"></a>CSacl (clase)

Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSacl : public CAcl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|El constructor.|
|[CSacl::~CSacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Agrega una entrada de control de acceso (ACE) de auditoría a la `CSacl` objeto.|
|[CSacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de acceso (ACE) en el `CSacl` objeto.|
|[CSacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la `CSacl` objeto.|
|[CSacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas en el `CSacl` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSacl::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Una SACL contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan los registros de auditoría en el registro de eventos de seguridad de un controlador de dominio. Tenga en cuenta que una SACL genera entradas de registro sólo en el controlador de dominio donde se produjo el intento de acceso, no en cada controlador de dominio que contiene una réplica del objeto.

Para establecer o recuperar la SACL del descriptor de seguridad de un objeto, el privilegio SE_SECURITY_NAME debe estar habilitado en el token de acceso del subproceso solicitante. El grupo Administradores tiene este privilegio concedido de forma predeterminada y se puede conceder a otros usuarios o grupos. Tener el privilegio concedido no es todo lo que es necesario: antes de poder realizar la operación definida por el privilegio, el privilegio debe estar habilitado en el token de acceso de seguridad para que surta efecto. El modelo permite privilegios habilita únicamente para las operaciones específicas del sistema y, a continuación, se deshabilitan cuando ya no son necesarios. Consulte [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl) para obtener ejemplos de la habilitación de SE_SECURITY_NAME.

Utilice los métodos de clase proporcionados para agregar, quitar, crear y eliminar las ACE de la `SACL` objeto. Vea también [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl).

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="addauditace"></a>  CSacl::AddAuditAce

Agrega una entrada de control de acceso (ACE) de auditoría a la `CSacl` objeto.

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
El [CSid](../../atl/reference/csid-class.md) objeto.

*AccessMask*<br/>
Especifica la máscara de derechos de acceso que se auditarán para el elemento especificado `CSid` objeto.

*bSuccess*<br/>
Especifica si los intentos de acceso permitidos se van a auditar. Establezca esta marca en True para habilitar la auditoría; en caso contrario, establézcalo en false.

*bFailure*<br/>
Especifica si los intentos de acceso denegado se van a auditar. Establezca esta marca en True para habilitar la auditoría; en caso contrario, establézcalo en false.

*AceFlags*<br/>
Un conjunto de marcas de bits que controlan la herencia de la ACE.

*pObjectType*<br/>
Tipo del objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ACE que se agrega a la `CSacl` objeto FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Un `CSacl` objeto contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan los registros de auditoría en el registro de eventos de seguridad. Este método agrega una entrada ACE para el `CSacl` objeto.

Consulte [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) para obtener una descripción de las diversas marcas que se pueden establecer en el *AceFlags* parámetro.

##  <a name="csacl"></a>  CSacl::CSacl

El constructor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Existente `ACL` estructura (lista de control de acceso).

### <a name="remarks"></a>Comentarios

El `CSacl` objeto se puede, opcionalmente, crear una existente `ACL` estructura. Asegúrese de que este parámetro es una lista de control de acceso del sistema (SACL) y no una lista de control de acceso discrecional (DACL). En las compilaciones de depuración, si se proporciona una DACL se producirá una aserción. En las versiones de lanzamiento se omiten todas las entradas de una DACL.

##  <a name="dtor"></a>  CSacl::~CSacl

Destructor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso (ACE).

##  <a name="getacecount"></a>  CSacl::GetAceCount

Devuelve el número de entradas de control de acceso (ACE) en el `CSacl` objeto.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de ACE contenidos en el `CSacl` objeto.

##  <a name="operator_eq"></a>  CSacl::operator =

Operador de asignación.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
El `ACL` (lista de control de acceso) para asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la actualización `CSacl` objeto. Asegúrese de que el `ACL` parámetro es realmente una lista de control de acceso de sistema (SACL) y no una lista de control de acceso discrecional (DACL). En las compilaciones de depuración se producirá una aserción y en las versiones de lanzamiento el `ACL` parámetro se omitirá.

##  <a name="removeace"></a>  CSacl::RemoveAce

Quita una ACE específica (entrada de control de acceso) de la `CSacl` objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE para quitar.

### <a name="remarks"></a>Comentarios

Este método se deriva [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

Quita todas las entradas de control de acceso (ACE) contenidas en el `CSacl` objeto.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Comentarios

Quita cada `ACE` estructura (si existe) en el `CSacl` objeto.

## <a name="see-also"></a>Vea también

[CAcl (clase)](../../atl/reference/cacl-class.md)<br/>
[ACLs](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
