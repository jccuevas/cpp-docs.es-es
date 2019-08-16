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
ms.openlocfilehash: 97ea2b8411b404caf9f833ad85f226d18aea1e73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496580"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Clase CPrivateObjectSecurityDesc

Esta clase representa un objeto de descriptor de seguridad de objeto privado.

## <a name="syntax"></a>Sintaxis

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|El constructor.|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Llame a este método para convertir un descriptor de seguridad y sus listas de control de acceso (ACL) a un formato que admita la propagación automática de entradas de control de acceso (ACE) heredables.|
|[CPrivateObjectSecurityDesc::Create](#create)|Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el administrador de recursos que realiza la llamada.|
|[CPrivateObjectSecurityDesc::Get](#get)|Llame a este método para recuperar información del descriptor de seguridad de un objeto privado.|
|[CPrivateObjectSecurityDesc::Set](#set)|Llame a este método para modificar el descriptor de seguridad de un objeto privado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Esta clase, que se deriva de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), proporciona métodos para crear y administrar el descriptor de seguridad de un objeto privado.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

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
Puntero a un objeto [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) que hace referencia al contenedor primario del objeto. Si no hay ningún contenedor primario, este parámetro es NULL.

*ObjectType*<br/>
Puntero a una `GUID` estructura que identifica el tipo de objeto asociado al objeto actual. Establezca *objecttype* en NULL si el objeto no tiene un GUID.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de True indica que el nuevo objeto es un contenedor. Un valor de False indica que el nuevo objeto no es un contenedor.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Este método intenta determinar si las ACE de la lista de control de acceso discrecional (DACL) y la lista de control de acceso del sistema (SACL) del descriptor de seguridad actual se heredaron del descriptor de seguridad primario. Llama a la función [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) .

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

El constructor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa el objeto `CPrivateObjectSecurityDesc`.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

Destructor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados y elimina el descriptor de seguridad del objeto privado.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

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
Puntero a un objeto [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) que hace referencia al directorio primario en el que se crea un nuevo objeto. Se establece en NULL si no hay ningún directorio primario.

*pCreator*<br/>
Puntero a un descriptor de seguridad proporcionado por el creador del objeto. Si el creador del objeto no pasa explícitamente la información de seguridad para el nuevo objeto, establezca este parámetro en NULL.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de True indica que el nuevo objeto es un contenedor. Un valor de False indica que el nuevo objeto no es un contenedor.

*Muestras*<br/>
Referencia al objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) para el proceso de cliente en cuyo nombre se crea el objeto.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*ObjectType*<br/>
Puntero a una `GUID` estructura que identifica el tipo de objeto asociado al objeto actual. Establezca *objecttype* en NULL si el objeto no tiene un GUID.

*bIsContainerObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor de True indica que el nuevo objeto es un contenedor. Un valor de False indica que el nuevo objeto no es un contenedor.

*AutoInheritFlags*<br/>
Conjunto de marcas de bits que controlan el modo en que las entradas de control de acceso (ACE) se heredan de *pParent*. Consulte [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) para obtener más información.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Este método llama a [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) o [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

El segundo método permite especificar el GUID del tipo de objeto del nuevo objeto o controlar cómo se heredan las ACE.

> [!NOTE]
>  Un descriptor de seguridad autorelativo es un descriptor de seguridad que almacena toda la información de seguridad en un bloque de memoria contiguo.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Llame a este método para recuperar información del descriptor de seguridad de un objeto privado.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Un conjunto de marcadores de bits que indican las partes del descriptor de seguridad que se van a recuperar. Este valor puede ser una combinación de las marcas de bits [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*pResult*<br/>
Puntero a un objeto [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) que recibe una copia de la información solicitada del descriptor de seguridad especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

El descriptor de seguridad es una estructura y datos asociados que contienen la información de seguridad para un objeto protegible.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Operador de asignación.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`CPrivateObjectSecurityDesc` Objeto que se va a asignar al objeto actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CPrivateObjectSecurityDesc` actualizado.

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

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
Un conjunto de marcadores de bits que indican las partes del descriptor de seguridad que se van a establecer. Este valor puede ser una combinación de las marcas de bits [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*Produzca*<br/>
Puntero a un objeto [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) . Las partes de este descriptor de seguridad indicadas por el parámetro *si* se aplican al descriptor de seguridad del objeto.

*GenericMapping*<br/>
Puntero a una estructura [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*Muestras*<br/>
Referencia al objeto [CAccessToken](../../atl/reference/caccesstoken-class.md) para el proceso de cliente en cuyo nombre se crea el objeto.

*AutoInheritFlags*<br/>
Conjunto de marcas de bits que controlan el modo en que las entradas de control de acceso (ACE) se heredan de *pParent*. Consulte [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) para obtener más información.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

El segundo método permite especificar el GUID del tipo de objeto del objeto o controlar cómo se heredan las ACE.

## <a name="see-also"></a>Vea también

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc (clase)](../../atl/reference/csecuritydesc-class.md)
