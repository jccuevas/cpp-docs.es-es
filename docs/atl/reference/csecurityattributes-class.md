---
title: Clase información
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 2139c25cb6d941d9debe0655ba91ba458b1f8c09
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915729"
---
# <a name="csecurityattributes-class"></a>Clase información

Esta clase es un contenedor fino para la estructura de atributos de seguridad.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Llame a este método para establecer los atributos del `CSecurityAttributes` objeto.|

## <a name="remarks"></a>Comentarios

La `SECURITY_ATTRIBUTES` estructura contiene un descriptor de [seguridad](/windows/desktop/api/winnt/ns-winnt-security_descriptor) que se usa para la creación de un objeto y especifica si el identificador recuperado mediante la especificación de esta estructura es heredable.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/desktop/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes

El constructor.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSecurityDescriptor*<br/>
Referencia a un descriptor de seguridad.

*bInheritsHandle*<br/>
Especifica si se hereda el identificador devuelto cuando se crea un nuevo proceso. Si este miembro es true, el nuevo proceso hereda el identificador.

##  <a name="set"></a>  CSecurityAttributes::Set

Llame a este método para establecer los atributos del `CSecurityAttributes` objeto.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSecurityDescriptor*<br/>
Referencia a un descriptor de seguridad.

*bInheritHandle*<br/>
Especifica si se hereda el identificador devuelto cuando se crea un nuevo proceso. Si este miembro es true, el nuevo proceso hereda el identificador.

### <a name="remarks"></a>Comentarios

El constructor utiliza este método para inicializar el `CSecurityAttributes` objeto.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descriptor de seguridad](/windows/desktop/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
