---
title: Clase CSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 90f8cfd66fbab88bfa29c39ff27189f02447a7c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496484"
---
# <a name="csecuritydesc-class"></a>Clase CSecurityDesc

Esta clase es un contenedor para la `SECURITY_DESCRIPTOR` estructura.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSecurityDesc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|El constructor.|
|[CSecurityDesc::~CSecurityDesc](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad válido y funcional.|
|[CSecurityDesc::GetControl](#getcontrol)|Recupera información de control del descriptor de seguridad.|
|[CSecurityDesc::GetDacl](#getdacl)|Recupera información de la lista de control de acceso discrecional (DACL) del descriptor de seguridad.|
|[CSecurityDesc::GetGroup](#getgroup)|Recupera la información del grupo primario del descriptor de seguridad.|
|[CSecurityDesc::GetOwner](#getowner)|Recupera la informatity del propietario del descriptor de seguridad.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Devuelve un puntero a la `SECURITY_DESCRIPTOR` estructura.|
|[CSecurityDesc::GetSacl](#getsacl)|Recupera información de la lista de control de acceso del sistema (SACL) del descriptor de seguridad.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Determina si la DACL está configurada para admitir la propagación automática.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Determina si el descriptor de seguridad está configurado con una DACL predeterminada.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Determina si el descriptor de seguridad contiene una DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Determina si la DACL está configurada para evitar modificaciones.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Determina si el identificador de seguridad de grupo (SID) del descriptor de seguridad se ha establecido de forma predeterminada.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Determina si el SID del propietario del descriptor de seguridad se estableció de forma predeterminada.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Determina si la SACL está configurada para admitir la propagación automática.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Determina si el descriptor de seguridad está configurado con una SACL predeterminada.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Determina si el descriptor de seguridad contiene una SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Determina si la SACL está configurada para evitar modificaciones.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Determina si el descriptor de seguridad está en formato autorelativo.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Llame a este método para convertir el descriptor de seguridad en formato absoluto.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Llame a este método para convertir el descriptor de seguridad en un formato autorelativo.|
|[CSecurityDesc::SetControl](#setcontrol)|Establece los bits de control de un descriptor de seguridad.|
|[CSecurityDesc::SetDacl](#setdacl)|Establece la información en una DACL. Si ya hay una DACL en el descriptor de seguridad, se reemplaza.|
|[CSecurityDesc::SetGroup](#setgroup)|Establece la información del grupo principal de un descriptor de seguridad de formato absoluto, reemplazando la información de grupo principal ya presente.|
|[CSecurityDesc::SetOwner](#setowner)|Establece la información de propietario de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de propietario ya presente.|
|[CSecurityDesc::SetSacl](#setsacl)|Establece la información en una SACL. Si ya hay una SACL en el descriptor de seguridad, se reemplaza.|
|[CSecurityDesc::ToString](#tostring)|Convierte un descriptor de seguridad en un formato de cadena.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSecurityDesc:: Operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Devuelve un puntero a la `SECURITY_DESCRIPTOR` estructura.|
|[CSecurityDesc::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

La `SECURITY_DESCRIPTOR` estructura contiene la información de seguridad asociada a un objeto. Las aplicaciones utilizan esta estructura para establecer y consultar el estado de seguridad de un objeto. Vea también [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Las aplicaciones no deben modificar `SECURITY_DESCRIPTOR` directamente la estructura y, en su lugar, deben usar los métodos de clase proporcionados.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

El constructor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto o `SECURITY_DESCRIPTOR` estructura que se va a asignar al `CSecurityDesc` nuevo objeto. `CSecurityDesc`

### <a name="remarks"></a>Comentarios

El `CSecurityDesc` objeto se puede crear opcionalmente mediante una `SECURITY_DESCRIPTOR` estructura o un objeto definido `CSecurityDesc` previamente.

##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc

Destructor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados.

##  <a name="fromstring"></a>  CSecurityDesc::FromString

Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad válido y funcional.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parámetros

*pstr*<br/>
Puntero a una cadena terminada en null que contiene el descriptor [de seguridad de formato de cadena](/windows/win32/SecAuthZ/security-descriptor-string-format) que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Devuelve verdadero si se realiza correctamente. Produce una excepción en caso de error.

### <a name="remarks"></a>Comentarios

La cadena se puede crear con [CSecurityDesc:: ToString](#tostring). Convertir el descriptor de seguridad en una cadena facilita el almacenamiento y la transmisión.

Este método llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

Recupera información de control del descriptor de seguridad.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parámetros

*psdc*<br/>
Puntero a una `SECURITY_DESCRIPTOR_CONTROL` estructura que recibe la información de control del descriptor de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false si se produce un error.

### <a name="remarks"></a>Comentarios

Este método llama a [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

Recupera información de la lista de control de acceso discrecional (DACL) del descriptor de seguridad.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDacl*<br/>
Puntero a una `CDacl` estructura en la que se va a almacenar una copia de la DACL del descriptor de seguridad. Si existe una ACL discrecional, el método establece *pDacl* en la dirección de la ACL discrecional del descriptor de seguridad. Si no existe una ACL discrecional, no se almacena ningún valor.

*pbPresent*<br/>
Puntero a un valor que indica la presencia de una ACL discrecional en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene una ACL discrecional, este parámetro se establece en true. Si el descriptor de seguridad no contiene una ACL discrecional, este parámetro se establece en false.

*pbDefaulted*<br/>
Puntero a una marca establecida en el valor de la marca SE_DACL_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura si existe una ACL discrecional para el descriptor de seguridad. Si esta marca es true, un mecanismo predeterminado recuperó la ACL discrecional. Si es false, el usuario especificó explícitamente la ACL discrecional.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false si se produce un error.

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

Recupera la información del grupo primario del descriptor de seguridad.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en CDacl.

*pbDefaulted*<br/>
Puntero a una marca establecida en el valor de la marca SE_GROUP_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura cuando el método devuelve.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false si se produce un error.

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

Recupera la informatity del propietario del descriptor de seguridad.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en CDacl.

*pbDefaulted*<br/>
Puntero a una marca establecida en el valor de la marca SE_OWNER_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura cuando el método devuelve.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false si se produce un error.

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

Devuelve un puntero a la `SECURITY_DESCRIPTOR` estructura.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la estructura [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) .

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

Recupera información de la lista de control de acceso del sistema (SACL) del descriptor de seguridad.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSacl*<br/>
Puntero a una `CSacl` estructura en la que se va a almacenar una copia de la SACL del descriptor de seguridad. Si existe una ACL del sistema, el método establece *pSacl* en la dirección de la ACL del sistema del descriptor de seguridad. Si no existe una ACL del sistema, no se almacena ningún valor.

*pbPresent*<br/>
Puntero a una marca que el método establece para indicar la presencia de una ACL del sistema en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene una ACL del sistema, este parámetro se establece en true. Si el descriptor de seguridad no contiene una ACL del sistema, este parámetro se establece en false.

*pbDefaulted*<br/>
Puntero a una marca establecida en el valor de la marca SE_SACL_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura si existe una ACL del sistema para el descriptor de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false si se produce un error.

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

Determina si la lista de control de acceso discrecional (DACL) está configurada para admitir la propagación automática.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL que está configurada para admitir la propagación automática de entradas de control de acceso (ACE) heredables a objetos secundarios existentes. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

Determina si el descriptor de seguridad está configurado con una lista de control de acceso discrecional (DACL) predeterminada.

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL predeterminada; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Esta marca puede afectar a la forma en que el sistema trata la DACL con respecto a la herencia de entradas de control de acceso (ACE). Por ejemplo, si el creador de un objeto no especifica una DACL, el objeto recibe la DACL predeterminada del token de acceso del creador. El sistema omite esta marca si no se establece la marca SE_DACL_PRESENT.

Esta marca se usa para determinar cómo se calculará la DACL final en el objeto y no se almacena físicamente en el control de descriptor de seguridad del objeto protegible.

Para establecer esta marca, use el método [CSecurityDesc:: SetDacl (](#setdacl) .

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

Determina si el descriptor de seguridad contiene una lista de control de acceso discrecional (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Si no se establece esta marca, o si se establece esta marca y la DACL es NULL, el descriptor de seguridad permite el acceso completo a todos los usuarios.

Esta marca se usa para contener la información de seguridad especificada por un llamador hasta que el descriptor de seguridad está asociado a un objeto protegible. Una vez que el descriptor de seguridad está asociado a un objeto protegible, la marca SE_DACL_PRESENT siempre se establece en el control de descriptor de seguridad.

Para establecer esta marca, use el método [CSecurityDesc:: SetDacl (](#setdacl) .

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

Determina si la lista de control de acceso discrecional (DACL) está configurada para evitar modificaciones.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la DACL está configurada para evitar que el descriptor de seguridad se modifique mediante entradas de control de acceso (ACE) heredables. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

Para establecer esta marca, use el método [CSecurityDesc:: SetDacl (](#setdacl) .

Este método admite la propagación automática de ACE heredables.

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

Determina si el identificador de seguridad de grupo (SID) del descriptor de seguridad se ha establecido de forma predeterminada.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si un mecanismo predeterminado, en lugar del proveedor original del descriptor de seguridad, proporcionó el SID del grupo del descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

Para establecer esta marca, use el método [CSecurityDesc:: SetGroup](#setgroup) .

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

Determina si el identificador de seguridad (SID) del propietario del descriptor de seguridad se ha establecido de forma predeterminada.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si un mecanismo predeterminado, en lugar del proveedor original del descriptor de seguridad, proporcionó el SID del propietario del descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

Para establecer esta marca, use el método [CSecurityDesc:: SetOwner](#setowner) .

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

Determina si la lista de control de acceso del sistema (SACL) está configurada para admitir la propagación automática.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL que está configurada para admitir la propagación automática de entradas de control de acceso (ACE) heredables a objetos secundarios existentes. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

Determina si el descriptor de seguridad está configurado con una lista de control de acceso (SACL) predeterminada del sistema.

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL predeterminada; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Esta marca puede afectar a la forma en que el sistema trata la SACL con respecto a la herencia de entradas de control de acceso (ACE). El sistema omite esta marca si no se establece la marca SE_SACL_PRESENT.

Para establecer esta marca, use el método [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

Determina si el descriptor de seguridad contiene una lista de control de acceso del sistema (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Para establecer esta marca, use el método [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

Determina si la lista de control de acceso del sistema (SACL) está configurada para evitar modificaciones.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la SACL está configurada para evitar que el descriptor de seguridad se modifique mediante entradas de control de acceso (ACE) heredables. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Comentarios

Para establecer esta marca, use el método [CSecurityDesc:: SetSacl](#setsacl) .

Este método admite la propagación automática de ACE heredables.

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

Determina si el descriptor de seguridad está en formato autorelativo.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad tiene un formato autorelativo con toda la información de seguridad en un bloque de memoria contiguo. Devuelve false si el descriptor de seguridad está en formato absoluto. Para obtener más información, consulte descriptores de [seguridad absoluta y autorelativo](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

Llame a este método para convertir el descriptor de seguridad en formato absoluto.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false en caso contrario.

### <a name="remarks"></a>Comentarios

Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de la propia información. Un descriptor de seguridad en formato autorelativo contiene la información de un bloque de memoria contiguo. En un descriptor de seguridad autorelativo `SECURITY_DESCRIPTOR` , una estructura siempre inicia la información, pero los demás componentes del descriptor de seguridad pueden seguir la estructura en cualquier orden. En lugar de utilizar direcciones de memoria, los componentes del descriptor de seguridad autorelativo se identifican mediante desplazamientos desde el principio del descriptor de seguridad. Este formato resulta útil cuando un descriptor de seguridad debe almacenarse en un disco o transmitirse por medio de un protocolo de comunicaciones. Para obtener más información, consulte descriptores de [seguridad absoluta y autorelativo](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

Llame a este método para convertir el descriptor de seguridad en un formato autorelativo.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se ejecuta correctamente, false en caso contrario.

### <a name="remarks"></a>Comentarios

Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de contener la información. Un descriptor de seguridad en formato autorelativo contiene la información de un bloque de memoria contiguo. En un descriptor de seguridad autorelativo `SECURITY_DESCRIPTOR` , una estructura siempre inicia la información, pero los demás componentes del descriptor de seguridad pueden seguir la estructura en cualquier orden. En lugar de usar direcciones de memoria, los componentes del descriptor de seguridad se identifican mediante desplazamientos desde el principio del descriptor de seguridad. Este formato resulta útil cuando un descriptor de seguridad debe almacenarse en un disco o transmitirse por medio de un protocolo de comunicaciones. Para obtener más información, consulte descriptores de [seguridad absoluta y autorelativo](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="operator_eq"></a>  CSecurityDesc::operator =

Operador de asignación.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`SECURITY_DESCRIPTOR` Estructura u `CSecurityDesc` objeto`CSecurityDesc` que se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CSecurityDesc` actualizado.

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: Operator const SECURITY_DESCRIPTOR *

Convierte un valor en un puntero a la `SECURITY_DESCRIPTOR` estructura.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

Establece los bits de control de un descriptor de seguridad.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parámetros

*ControlBitsOfInterest*<br/>
Máscara SECURITY_DESCRIPTOR_CONTROL que indica los bits de control que se van a establecer. Para obtener una lista de las marcas que se pueden establecer, vea [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Una máscara SECURITY_DESCRIPTOR_CONTROL que indica los nuevos valores de los bits de control especificados por la máscara *ControlBitsOfInterest* . Este parámetro puede ser una combinación de las marcas enumeradas para el parámetro *ControlBitsOfInterest* .

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Este método llama a [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

Establece la información en una lista de control de acceso discrecional (DACL). Si ya hay una DACL en el descriptor de seguridad, se reemplaza.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*DACL*<br/>
Referencia a un `CDacl` objeto que especifica la DACL para el descriptor de seguridad. Este parámetro no debe ser NULL. Para establecer una DACL NULL en el descriptor de seguridad, se debe usar la primera forma del método con *bPresent* establecido en false.

*bPresent*<br/>
Especifica una marca que indica la presencia de una DACL en el descriptor de seguridad. Si este parámetro es true, el método establece la marca SE_DACL_PRESENT en la `SECURITY_DESCRIPTOR_CONTROL` estructura y usa los valores de los parámetros *DACL* y *bDefaulted* . Si es false, el método borra la marca SE_DACL_PRESENT y *bDefaulted* se omite.

*bDefaulted*<br/>
Especifica una marca que indica el origen de la DACL. Si esta marca es true, algún mecanismo predeterminado ha recuperado la DACL. Si es false, el usuario ha especificado explícitamente la DACL. El método almacena este valor en la marca SE_DACL_DEFAULTED de la `SECURITY_DESCRIPTOR_CONTROL` estructura. Si no se especifica este parámetro, se borra la marca SE_DACL_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Existe una diferencia importante entre una DACL vacía y una no existente. Cuando una DACL está vacía, no contiene entradas de control de acceso y no se ha concedido explícitamente ningún derecho de acceso. Como resultado, se deniega implícitamente el acceso al objeto. Si un objeto no tiene DACL, por otro lado, no se asigna ninguna protección al objeto y se concede cualquier solicitud de acceso.

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

Establece la información del grupo principal de un descriptor de seguridad de formato absoluto, reemplazando la información de grupo principal ya presente.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Junction*<br/>
Referencia a un objeto [CSid](../../atl/reference/csid-class.md) para el nuevo grupo primario del descriptor de seguridad. Este parámetro no debe ser NULL. Un descriptor de seguridad se puede marcar como sin DACL o SACL, pero debe tener un grupo y un propietario, incluso este es el SID nulo (que es un SID integrado con un significado especial).

*bDefaulted*<br/>
Indica si la información del grupo principal se ha derivado de un mecanismo predeterminado. Si este valor es true, es información predeterminada y el método almacena este valor como la marca SE_GROUP_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura. Si este parámetro es cero, se borra la marca SE_GROUP_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

Establece la información de propietario de un descriptor de seguridad de formato absoluto. Reemplaza cualquier información de propietario ya presente.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Junction*<br/>
El objeto [CSid](../../atl/reference/csid-class.md) del nuevo propietario primario del descriptor de seguridad. Este parámetro no debe ser NULL.

*bDefaulted*<br/>
Indica si la información de propietario se deriva de un mecanismo predeterminado. Si este valor es true, se trata de información predeterminada. El método almacena este valor como la marca SE_OWNER_DEFAULTED en la `SECURITY_DESCRIPTOR_CONTROL` estructura. Si este parámetro es cero, se borra la marca SE_OWNER_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

Establece información en una lista de control de acceso del sistema (SACL). Si ya hay una SACL en el descriptor de seguridad, se reemplaza.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*SACL*<br/>
Puntero a un `CSacl` objeto que especifica la SACL del descriptor de seguridad. Este parámetro no debe ser NULL y debe ser un objeto CSacl. A diferencia de las DACL, no hay ninguna diferencia entre NULL y una SACL vacía, ya que los objetos SACL no especifican derechos de acceso, solo información de auditoría.

*bDefaulted*<br/>
Especifica una marca que indica el origen de la SACL. Si esta marca es true, algún mecanismo predeterminado ha recuperado la SACL. Si es false, el usuario ha especificado explícitamente la SACL. El método almacena este valor en la marca SE_SACL_DEFAULTED de la `SECURITY_DESCRIPTOR_CONTROL` estructura. Si no se especifica este parámetro, se borra la marca SE_SACL_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

##  <a name="tostring"></a>  CSecurityDesc::ToString

Convierte un descriptor de seguridad en un formato de cadena.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pstr*<br/>
Puntero a una cadena terminada en null que recibirá el descriptor [de seguridad de formato de cadena](/windows/win32/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Especifica una combinación de marcas de bits SECURITY_INFORMATION para indicar los componentes del descriptor de seguridad que se van a incluir en la cadena de salida.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

Una vez que el descriptor de seguridad está en formato de cadena, puede almacenarse o transmitirse más fácilmente. Use el `CSecurityDesc::FromString` método para volver a convertir la cadena en un descriptor de seguridad.

El parámetro *si* puede contener las siguientes marcas SECURITY_INFORMATION:

|Value|Significado|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Incluya el propietario.|
|GROUP_SECURITY_INFORMATION|Incluya el grupo principal.|
|DACL_SECURITY_INFORMATION|Incluya la DACL.|
|SACL_SECURITY_INFORMATION|Incluya la SACL.|

Si DACL es NULL y el bit de control SE_DACL_PRESENT se establece en el descriptor de seguridad de entrada, se produce un error en el método.

Si DACL es NULL y el bit de control SE_DACL_PRESENT no se establece en el descriptor de seguridad de entrada, la cadena de descriptor de seguridad resultante no tiene un componente D:. Consulte [formato de cadena](/windows/win32/SecAuthZ/security-descriptor-string-format) de descriptor de seguridad para obtener más detalles.

Este método llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
