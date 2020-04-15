---
title: Clase CSecurityAttributes
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 113bcebb7461415590156206ee7aa4c91e0e93d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330988"
---
# <a name="csecurityattributes-class"></a>Clase CSecurityAttributes

Esta clase es un contenedor fino para la estructura de atributos de seguridad.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Llame a este método para `CSecurityAttributes` establecer los atributos del objeto.|

## <a name="remarks"></a>Observaciones

La `SECURITY_ATTRIBUTES` estructura contiene un descriptor de [seguridad](/windows/win32/api/winnt/ns-winnt-security_descriptor) utilizado para la creación de un objeto y especifica si el identificador recuperado especificando esta estructura es heredable.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

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

## <a name="csecurityattributesset"></a><a name="set"></a>CSecurityAttributes::Set

Llame a este método para `CSecurityAttributes` establecer los atributos del objeto.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSecurityDescriptor*<br/>
Referencia a un descriptor de seguridad.

*bInheritHandle*<br/>
Especifica si se hereda el identificador devuelto cuando se crea un nuevo proceso. Si este miembro es true, el nuevo proceso hereda el identificador.

### <a name="remarks"></a>Observaciones

El constructor utiliza este método `CSecurityAttributes` para inicializar el objeto.

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descriptor de seguridad](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
