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
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326033"
---
# <a name="security-global-functions"></a>Funciones globales de seguridad

Estas funciones proporcionan compatibilidad para modificar objetos SID y ACL.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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

**Encabezado:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl

Llame a esta función para recuperar la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controlar el objeto para el que se va a recuperar la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*pDacl*<br/>
Puntero a un objeto DACL que contendrá la información de seguridad recuperada.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *hObject* o *pDacl* no es válido.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>AtlSetDacl

Llame a esta función para definir la información de la lista de control de acceso discrecional (DACL) de un objeto especificado.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controlar el objeto para el que se va a establecer la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*rDacl*<br/>
La DACL que contiene la nueva información de seguridad.

*dwInheritanceFlowControl*<br/>
El control de flujo de herencia. Este valor puede ser 0 (valor predeterminado), PROTECTED_DACL_SECURITY_INFORMATION o UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *hObject* no es válido o si *dwInheritanceFlowControl* no es uno de los tres valores permitidos.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid

Llame a esta función para recuperar el identificador de seguridad (SID) de grupo de un objeto.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controle el objeto desde el que se va a recuperar información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*Psid*<br/>
Puntero a `CSid` un objeto que contendrá la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid

Llame a esta función para definir el identificador de seguridad (SID) de grupo de un objeto.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controlar el objeto para el que se va a establecer la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*rSid*<br/>
Objeto `CSid` que contiene la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

Llame a esta función para recuperar el identificador de seguridad (SID) del propietario de un objeto.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controle el objeto desde el que se va a recuperar información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*Psid*<br/>
Puntero a `CSid` un objeto que contendrá la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

Llame a esta función para definir el identificador de seguridad (SID) del propietario de un objeto.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controlar el objeto para el que se va a establecer la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*rSid*<br/>
Objeto `CSid` que contiene la nueva información de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>AtlGetSacl

Llame a esta función para recuperar la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Controle el objeto desde el que se va a recuperar la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*pSacl*<br/>
Puntero a un objeto SACL que contendrá la información de seguridad recuperada.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Si `AtlGetSacl` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>AtlSetSacl

Llame a esta función para definir la información de la lista de control de acceso del sistema (SACL) de un objeto especificado.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

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
Controlar el objeto para el que se va a establecer la información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el *hObject* parámetro.

*rSacl*<br/>
La SACL que contiene la nueva información de seguridad.

*dwInheritanceFlowControl*<br/>
El control de flujo de herencia. Este valor puede ser 0 (valor predeterminado), PROTECTED_SACL_SECURITY_INFORMATION o UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *hObject* no es válido o si *dwInheritanceFlowControl* no es uno de los tres valores permitidos.

Si `AtlSetSacl` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor

Llame a esta función para recuperar el descriptor de seguridad de un objeto especificado.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

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
Puntero a una cadena terminada en null que especifica el nombre del objeto desde el que se va a recuperar información de seguridad.

*Objecttype*<br/>
Especifica un valor de la [enumeración SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) que indica el tipo de objeto identificado por el parámetro *pszObjectName.*

*pSecurityDescriptor*<br/>
Objeto que recibe el descriptor de seguridad solicitado.

*requestedInfo*<br/>
Conjunto de [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) indicadores de bits que indican el tipo de información de seguridad que se va a recuperar. Este parámetro puede ser una combinación de los siguientes valores.

*bRequestNeededPrivileges*<br/>
Si es true, la función intentará habilitar el privilegio SE_SECURITY_NAME y restaurarlo al finalizar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Si `AtlGetSecurityDescriptor` se va a llamar muchas veces en muchos objetos diferentes, será más eficaz habilitar el privilegio SE_SECURITY_NAME una vez antes de llamar a la función, con *bRequestNeededPrivileges* establecido en false.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
