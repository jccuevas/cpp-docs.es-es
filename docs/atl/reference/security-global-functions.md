---
title: Funciones globales de seguridad
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 5f3c0464b239f4500d416b80ae4fdf06c2dc386f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495177"
---
# <a name="security-global-functions"></a>Funciones globales de seguridad

Estas funciones proporcionan compatibilidad para modificar los objetos de SID y ACL.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Llame a esta función para recuperar la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.|
|[AtlSetDacl](#atlsetdacl)|Llame a esta función para definir la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.|
|[AtlGetGroupSid](#atlgetgroupsid)|Llame a esta función para recuperar el identificador de seguridad (SID) de grupo de un objeto.|
|[AtlSetGroupSid](#atlsetgroupsid)|Llame a esta función para definir el identificador de seguridad (SID) de grupo de un objeto.|
|[AtlGetOwnerSid](#atlgetownersid)|Llame a esta función para recuperar el identificador de seguridad (SID) del propietario de un objeto.|
|[AtlSetOwnerSid](#atlsetownersid)|Llame a esta función para definir el identificador de seguridad (SID) del propietario de un objeto.|
|[AtlGetSacl](#atlgetsacl)|Llame a esta función para recuperar la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.|
|[AtlSetSacl](#atlsetsacl)|Llame a esta función para definir la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Llame a esta función para recuperar el descriptor de seguridad de un objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlgetdacl"></a>  AtlGetDacl

Llame a esta función para recuperar la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto para el que se va a recuperar la información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*pDacl*<br/>
Puntero a un objeto DACL que contendrá la información de seguridad recuperada.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *hObject* o *pDacl* no son válidos.

##  <a name="atlsetdacl"></a>  AtlSetDacl

Llame a esta función para definir la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto para el que se va a establecer información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*rDacl*<br/>
DACL que contiene la nueva información de seguridad.

*dwInheritanceFlowControl*<br/>
Control de flujo de herencia. Este valor puede ser 0 (el valor predeterminado), PROTECTED_DACL_SECURITY_INFORMATION o UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *hObject* no es válido o si *dwInheritanceFlowControl* no es uno de los tres valores permitidos.
### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid

Llame a esta función para recuperar el identificador de seguridad (SID) de grupo de un objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto del que se va a recuperar información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*pSid*<br/>
Puntero a un `CSid` objeto que contendrá la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid

Llame a esta función para definir el identificador de seguridad (SID) de grupo de un objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto para el que se va a establecer información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*rSid*<br/>
`CSid` Objeto que contiene la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid

Llame a esta función para recuperar el identificador de seguridad (SID) del propietario de un objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto del que se va a recuperar información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*pSid*<br/>
Puntero a un `CSid` objeto que contendrá la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid

Llame a esta función para definir el identificador de seguridad (SID) del propietario de un objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto para el que se va a establecer información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*rSid*<br/>
`CSid` Objeto que contiene la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlgetsacl"></a>  AtlGetSacl

Llame a esta función para recuperar la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto del que se va a recuperar la información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*pSacl*<br/>
Puntero a un objeto SACL que contendrá la información de seguridad recuperada.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Si `AtlGetSacl` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlsetsacl"></a>  AtlSetSacl

Llame a esta función para definir la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador del objeto para el que se va a establecer información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *hObject* .

*rSacl*<br/>
SACL que contiene la nueva información de seguridad.

*dwInheritanceFlowControl*<br/>
Control de flujo de herencia. Este valor puede ser 0 (el valor predeterminado), PROTECTED_SACL_SECURITY_INFORMATION o UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *hObject* no es válido o si *dwInheritanceFlowControl* no es uno de los tres valores permitidos.

Si `AtlSetSacl` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor

Llame a esta función para recuperar el descriptor de seguridad de un objeto especificado.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszObjectName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del objeto del que se va a recuperar la información de seguridad.

*ObjectType*<br/>
Especifica un valor de la enumeración [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *pszObjectName* .

*pSecurityDescriptor*<br/>
Objeto que recibe el descriptor de seguridad solicitado.

*requestedInfo*<br/>
Un conjunto de marcas de bits [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) que indican el tipo de información de seguridad que se va a recuperar. Este parámetro puede ser una combinación de los valores siguientes.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Si `AtlGetSecurityDescriptor` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
