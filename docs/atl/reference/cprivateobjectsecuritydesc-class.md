---
title: Clase CPrivateObjectSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331417"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Clase CPrivateObjectSecurityDesc

Esta clase representa un objeto descriptor de seguridad de objeto privado.

## <a name="syntax"></a>Sintaxis

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|El constructor.|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Llame a este método para convertir un descriptor de seguridad y sus listas de control de acceso (ACL) a un formato que admita la propagación automática de entradas de control de acceso (ACE) heredables.|
|[CPrivateObjectSecurityDesc::Create](#create)|Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el administrador de recursos que realiza la llamada.|
|[CPrivateObjectSecurityDesc::Get](#get)|Llame a este método para recuperar información del descriptor de seguridad de un objeto privado.|
|[CPrivateObjectSecurityDesc::Set](#set)|Llame a este método para modificar el descriptor de seguridad de un objeto privado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador a la operadora de la red](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

Esta clase, derivada de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), proporciona métodos para crear y administrar el descriptor de seguridad de un objeto privado.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit

Llame a este método para convertir un descriptor de seguridad y sus listas de control de acceso (ACL) a un formato que admita la propagación automática de entradas de control de acceso (ACE) heredables.

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia al contenedor primario del objeto. Si no hay ningún contenedor primario, este parámetro es NULL.

*Objecttype*<br/>
Puntero a `GUID` una estructura que identifica el tipo de objeto asociado al objeto actual. Establezca *ObjectType en* NULL si el objeto no tiene un GUID.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Este método intenta determinar si las ACE de la lista de control de acceso discrecional (DACL) y la lista de control de acceso del sistema (SACL) del descriptor de seguridad actual se heredaron del descriptor de seguridad primario. Llama a la función [ConvertToAutoInheritPrivateObjectSecurity.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

El constructor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el objeto `CPrivateObjectSecurityDesc`.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Destructor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos asignados y elimina el descriptor de seguridad del objeto privado.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Create

Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el administrador de recursos que realiza la llamada.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia al directorio primario en el que se crea un nuevo objeto. Establezca en NULL si no hay ningún directorio primario.

*pCreator*<br/>
Puntero a un descriptor de seguridad proporcionado por el creador del objeto. Si el creador del objeto no pasa explícitamente información de seguridad para el nuevo objeto, establezca este parámetro en NULL.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.

*Token*<br/>
Referencia al objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) para el proceso de cliente en cuyo nombre se está creando el objeto.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*Objecttype*<br/>
Puntero a `GUID` una estructura que identifica el tipo de objeto asociado al objeto actual. Establezca *ObjectType en* NULL si el objeto no tiene un GUID.

*bIsContainerObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.

*AutoInheritFlags*<br/>
Conjunto de indicadores de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de *pParent*. Consulte [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Este método llama a [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) o [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

El segundo método permite especificar el GUID de tipo de objeto del nuevo objeto o controlar cómo se heredan las ACE.

> [!NOTE]
> Un descriptor de seguridad autorelativo es un descriptor de seguridad que almacena toda su información de seguridad en un bloque contiguo de memoria.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get

Llame a este método para recuperar información del descriptor de seguridad de un objeto privado.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Conjunto de indicadores de bits que indican las partes del descriptor de seguridad que se van a recuperar. Este valor puede ser una combinación de los indicadores de bits [SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*pResult*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que recibe una copia de la información solicitada desde el descriptor de seguridad especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

El descriptor de seguridad es una estructura y datos asociados que contiene la información de seguridad de un objeto protegible.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator ?

Operador de asignación.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CPrivateObjectSecurityDesc` que se va a asignar al objeto actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CPrivateObjectSecurityDesc` objeto actualizado.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set

Llame a este método para modificar el descriptor de seguridad de un objeto privado.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Conjunto de indicadores de bits que indican las partes del descriptor de seguridad que se va a establecer. Este valor puede ser una combinación de los indicadores de bits [SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*Modificación*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto. Las partes de este descriptor de seguridad indicadas por el parámetro *si* se aplican al descriptor de seguridad del objeto.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*Token*<br/>
Referencia al objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) para el proceso de cliente en cuyo nombre se está creando el objeto.

*AutoInheritFlags*<br/>
Conjunto de indicadores de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de *pParent*. Consulte [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

El segundo método permite especificar el GUID de tipo de objeto del objeto o controlar cómo se heredan las ACE.

## <a name="see-also"></a>Consulte también

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[Clase CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
