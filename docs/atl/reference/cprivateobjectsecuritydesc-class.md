---
title: CPrivateObjectSecurityDesc (clase)
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
ms.openlocfilehash: 2617113f2805f8d1c56e7fa6cbebfe669709c100
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694041"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc (clase)

Esta clase representa un objeto de descriptor de seguridad de objeto privado.

## <a name="syntax"></a>Sintaxis

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|El constructor.|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Llame a este método para convertir un descriptor de seguridad y las listas de control de acceso (ACL) en un formato que admite la propagación automática de entradas de control de acceso heredable (ACE).|
|[CPrivateObjectSecurityDesc::Create](#create)|Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el Administrador de recursos que realiza la llamada.|
|[CPrivateObjectSecurityDesc::Get](#get)|Llame a este método para recuperar información de descriptor de seguridad de un objeto privado.|
|[CPrivateObjectSecurityDesc::Set](#set)|Llame a este método para modificar el descriptor de seguridad de un objeto privado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Esta clase, derivada de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), proporciona métodos para crear y administrar el descriptor de seguridad de un objeto privado.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Llame a este método para convertir un descriptor de seguridad y las listas de control de acceso (ACL) en un formato que admite la propagación automática de entradas de control de acceso heredable (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia el contenedor primario del objeto. Si no hay ningún contenedor primario, este parámetro es NULL.

*ObjectType*<br/>
Puntero a un `GUID` estructura que identifica el tipo de objeto asociado al objeto actual. Establecer *ObjectType* en NULL si el objeto no tiene un GUID.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor true indica que el nuevo objeto es un contenedor. Un valor false indica que el nuevo objeto no es un contenedor.

*GenericMapping*<br/>
Puntero a un [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) estructura que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Este método intenta determinar si la lista de las ACE en el control de acceso discrecional (DACL) y una lista de control de acceso de sistema (SACL) del descriptor de seguridad actual se heredan el descriptor de seguridad del elemento primario. Lo llama el [ConvertToAutoInheritPrivateObjectSecurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) función.

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

El constructor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa el objeto `CPrivateObjectSecurityDesc`.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc

Destructor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados y elimina el descriptor de seguridad del objeto privado.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el Administrador de recursos que realiza la llamada.

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
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia el directorio principal en que se se crea un nuevo objeto. Se establece en NULL si no hay ningún directorio primario.

*pCreator*<br/>
Puntero a un descriptor de seguridad proporcionado por el creador del objeto. Si el creador del objeto no pasar explícitamente información de seguridad para el nuevo objeto, establezca este parámetro en NULL.

*bIsDirectoryObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor true indica que el nuevo objeto es un contenedor. Un valor false indica que el nuevo objeto no es un contenedor.

*símbolo (token)*<br/>
Hacer referencia a la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para el proceso de cliente en cuyo nombre se está creando el objeto.

*GenericMapping*<br/>
Puntero a un [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) estructura que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*ObjectType*<br/>
Puntero a un `GUID` estructura que identifica el tipo de objeto asociado al objeto actual. Establecer *ObjectType* en NULL si el objeto no tiene un GUID.

*bIsContainerObject*<br/>
Especifica si el nuevo objeto puede contener otros objetos. Un valor true indica que el nuevo objeto es un contenedor. Un valor false indica que el nuevo objeto no es un contenedor.

*AutoInheritFlags*<br/>
Un conjunto de marcas de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de *pParent*. Consulte [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Este método llama a [CreatePrivateObjectSercurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) o [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581).

El segundo método permite especificar el tipo de objeto GUID del nuevo objeto o controlar cómo se heredan las ACE.

> [!NOTE]
>  Un descriptor de seguridad autorelativo es un descriptor de seguridad que almacena toda su información de seguridad en un bloque de memoria contiguo.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Llame a este método para recuperar información de descriptor de seguridad de un objeto privado.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parámetros

*Si*<br/>
Un conjunto de marcas de bits que indican las partes del descriptor de seguridad para recuperar. Este valor puede ser una combinación de la [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) marcas de bits.

*pResult*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que recibe una copia de la información solicitada del descriptor de seguridad especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

El descriptor de seguridad es una estructura y los datos asociados que contiene la información de seguridad para un objeto protegible.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Operador de asignación.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*RHS*<br/>
La `CPrivateObjectSecurityDesc` objeto que se va a asignar al objeto actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el texto actualizado `CPrivateObjectSecurityDesc` objeto.

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

*Si*<br/>
Un conjunto de marcas de bits que indican las partes del descriptor de seguridad para establecer. Este valor puede ser una combinación de la [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) marcas de bits.

*Modificación*<br/>
Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto. Las partes de este descriptor de seguridad indican por el *si* parámetro se aplica al descriptor de seguridad del objeto.

*GenericMapping*<br/>
Puntero a un [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) estructura que especifica la asignación de cada derecho genérico a derechos específicos para el objeto.

*símbolo (token)*<br/>
Hacer referencia a la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para el proceso de cliente en cuyo nombre se está creando el objeto.

*AutoInheritFlags*<br/>
Un conjunto de marcas de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de *pParent*. Consulte [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

El segundo método permite especificar el GUID del tipo de objeto del objeto o controlar cómo se heredan las ACE.

## <a name="see-also"></a>Vea también

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc (clase)](../../atl/reference/csecuritydesc-class.md)
