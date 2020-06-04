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
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330975"
---
# <a name="csecuritydesc-class"></a>Clase CSecurityDesc

Esta clase es un `SECURITY_DESCRIPTOR` contenedor para la estructura.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSecurityDesc
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|El constructor.|
|[CSecurityDesc::CSecurityDesc](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad funcional válido.|
|[CSecurityDesc::GetControl](#getcontrol)|Recupera información de control del descriptor de seguridad.|
|[CSecurityDesc::GetDacl](#getdacl)|Recupera información discrecional de la lista de control de acceso (DACL) del descriptor de seguridad.|
|[CSecurityDesc::GetGroup](#getgroup)|Recupera la información del grupo principal del descriptor de seguridad.|
|[CSecurityDesc::GetOwner](#getowner)|Recupera el propietario informaton del descriptor de seguridad.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Devuelve un puntero `SECURITY_DESCRIPTOR` a la estructura.|
|[CSecurityDesc::GetSacl](#getsacl)|Recupera información de la lista de control de acceso del sistema (SACL) del descriptor de seguridad.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Determina si el DACL está configurado para soportar la propagación automática.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Determina si el descriptor de seguridad está configurado con una DACL predeterminada.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Determina si el descriptor de seguridad contiene una DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Determina si la DACL está configurada para evitar modificaciones.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Determina si el identificador de seguridad de grupo (SID) del descriptor de seguridad se estableció de forma predeterminada.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Determina si el SID propietario del descriptor de seguridad se estableció de forma predeterminada.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Determina si la SACL está configurada para admitir la propagación automática.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Determina si el descriptor de seguridad está configurado con una SACL predeterminada.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Determina si el descriptor de seguridad contiene una SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Determina si la SACL está configurada para evitar modificaciones.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Determina si el descriptor de seguridad está en formato autorelativo.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Llame a este método para convertir el descriptor de seguridad al formato absoluto.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Llame a este método para convertir el descriptor de seguridad a formato autorelativo.|
|[CSecurityDesc::SetControl](#setcontrol)|Establece los bits de control de un descriptor de seguridad.|
|[CSecurityDesc::SetDacl](#setdacl)|Establece la información en una DACL. Si una DACL ya está presente en el descriptor de seguridad, se reemplaza.|
|[CSecurityDesc::SetGroup](#setgroup)|Establece la información de grupo principal de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de grupo principal ya presente.|
|[CSecurityDesc::SetOwner](#setowner)|Establece la información de propietario de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de propietario ya presente.|
|[CSecurityDesc::SetSacl](#setsacl)|Establece la información en una SACL. Si una SACL ya está presente en el descriptor de seguridad, se reemplaza.|
|[CSecurityDesc::ToString](#tostring)|Convierte un descriptor de seguridad en un formato de cadena.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Devuelve un puntero `SECURITY_DESCRIPTOR` a la estructura.|
|[CSecurityDesc::operador ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

La `SECURITY_DESCRIPTOR` estructura contiene la información de seguridad asociada a un objeto. Las aplicaciones usan esta estructura para establecer y consultar el estado de seguridad de un objeto. Vea también [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Las aplicaciones no `SECURITY_DESCRIPTOR` deben modificar la estructura directamente y, en su lugar, deben usar los métodos de clase proporcionados.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

El constructor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CSecurityDesc` o `SECURITY_DESCRIPTOR` estructura que se `CSecurityDesc` va a asignar al nuevo objeto.

### <a name="remarks"></a>Observaciones

El `CSecurityDesc` objeto se puede crear `SECURITY_DESCRIPTOR` opcionalmente utilizando una estructura o un objeto definido `CSecurityDesc` previamente.

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc::CSecurityDesc

Destructor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos asignados.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::FromString

Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad funcional válido.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parámetros

*Pstr*<br/>
Puntero a una cadena terminada en null que contiene el descriptor de [seguridad de formato](/windows/win32/SecAuthZ/security-descriptor-string-format) de cadena que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Devuelve true en caso de éxito. Produce una excepción en caso de error.

### <a name="remarks"></a>Observaciones

La cadena se puede crear mediante [CSecurityDesc::ToString](#tostring). La conversión del descriptor de seguridad en una cadena facilita el almacenamiento y la transmisión.

Este método llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::GetControl

Recupera información de control del descriptor de seguridad.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parámetros

*psdc*<br/>
Puntero a `SECURITY_DESCRIPTOR_CONTROL` una estructura que recibe la información de control del descriptor de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false si se produce un error.

### <a name="remarks"></a>Observaciones

Este método llama a [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl

Recupera información discrecional de la lista de control de acceso (DACL) del descriptor de seguridad.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDacl*<br/>
Puntero a `CDacl` una estructura en la que almacenar una copia de la DACL del descriptor de seguridad. Si existe una ACL discrecional, el método establece *pDacl* en la dirección de la ACL discrecional del descriptor de seguridad. Si no existe una ACL discrecional, no se almacena ningún valor.

*pbPresent*<br/>
Puntero a un valor que indica la presencia de una ACL discrecional en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene una ACL discrecional, este parámetro se establece en true. Si el descriptor de seguridad no contiene una ACL discrecional, este parámetro se establece en false.

*pbDefaulted*<br/>
Puntero a un indicador establecido en el `SECURITY_DESCRIPTOR_CONTROL` valor de la SE_DACL_DEFAULTED marca en la estructura si existe una ACL discrecional para el descriptor de seguridad. Si este indicador es true, la ACL discrecional fue recuperada por un mecanismo predeterminado; si es false, un usuario especificó explícitamente la ACL discrecional.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false si se produce un error.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::GetGroup

Recupera la información del grupo principal del descriptor de seguridad.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en el CDacl.

*pbDefaulted*<br/>
Puntero a una marca establecida en el `SECURITY_DESCRIPTOR_CONTROL` valor de la SE_GROUP_DEFAULTED marca en la estructura cuando se devuelve el método.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false si se produce un error.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::GetOwner

Recupera el propietario informaton del descriptor de seguridad.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en el CDacl.

*pbDefaulted*<br/>
Puntero a una marca establecida en el `SECURITY_DESCRIPTOR_CONTROL` valor de la SE_OWNER_DEFAULTED marca en la estructura cuando se devuelve el método.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false si se produce un error.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Devuelve un puntero `SECURITY_DESCRIPTOR` a la estructura.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [estructura SECURITY_DESCRIPTOR.](/windows/win32/api/winnt/ns-winnt-security_descriptor)

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl

Recupera información de la lista de control de acceso del sistema (SACL) del descriptor de seguridad.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSacl*<br/>
Puntero a `CSacl` una estructura en la que almacenar una copia de la SACL del descriptor de seguridad. Si existe una ACL del sistema, el método establece *pSacl* en la dirección de la ACL del sistema del descriptor de seguridad. Si no existe una ACL del sistema, no se almacena ningún valor.

*pbPresent*<br/>
Puntero a una marca del método se establece para indicar la presencia de una ACL del sistema en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene una ACL del sistema, este parámetro se establece en true. Si el descriptor de seguridad no contiene una ACL del sistema, este parámetro se establece en false.

*pbDefaulted*<br/>
Puntero a un indicador establecido en el `SECURITY_DESCRIPTOR_CONTROL` valor del indicador SE_SACL_DEFAULTED en la estructura si existe una ACL del sistema para el descriptor de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false si se produce un error.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Determina si la lista de control de acceso discrecional (DACL) está configurada para admitir la propagación automática.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL que está configurada para admitir la propagación automática de entradas de control de acceso (ACE) heredables a objetos secundarios existentes. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Determina si el descriptor de seguridad está configurado con una lista de control de acceso discrecional (DACL) predeterminada.

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL predeterminada, false en caso contrario.

### <a name="remarks"></a>Observaciones

Este indicador puede afectar a cómo el sistema trata la DACL, con respecto a la herencia de entrada de control de acceso (ACE). Por ejemplo, si el creador de un objeto no especifica una DACL, el objeto recibe la DACL predeterminada del token de acceso del creador. El sistema ignora esta marca si no se establece el indicador SE_DACL_PRESENT.

Este indicador se utiliza para determinar cómo se va a calcular la DACL final en el objeto y no se almacena físicamente en el control descriptor de seguridad del objeto protegible.

Para establecer esta marca, utilice el [CSecurityDesc::SetDacl](#setdacl) método.

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Determina si el descriptor de seguridad contiene una lista de control de acceso discrecional (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una DACL, false en caso contrario.

### <a name="remarks"></a>Observaciones

Si no se establece esta marca, o si se establece esta marca y la DACL es NULL, el descriptor de seguridad permite el acceso completo a todos.

Este indicador se utiliza para contener la información de seguridad especificada por un llamador hasta que el descriptor de seguridad está asociado a un objeto protegible. Una vez que el descriptor de seguridad está asociado a un objeto protegible, el indicador SE_DACL_PRESENT siempre se establece en el control descriptor de seguridad.

Para establecer esta marca, utilice el [CSecurityDesc::SetDacl](#setdacl) método.

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected

Determina si la lista de control de acceso discrecional (DACL) está configurada para evitar modificaciones.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la DACL está configurada para evitar que las entradas de control de acceso (ACE) heredables modifiquen el descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

Para establecer esta marca, utilice el [CSecurityDesc::SetDacl](#setdacl) método.

Este método admite la propagación automática de ACE heredables.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Determina si el identificador de seguridad de grupo (SID) del descriptor de seguridad se estableció de forma predeterminada.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si un mecanismo predeterminado, en lugar del proveedor original del descriptor de seguridad, proporciona el SID de grupo del descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

Para establecer esta marca, utilice el [CSecurityDesc::SetGroup](#setgroup) método.

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Determina si el identificador de seguridad del propietario (SID) del descriptor de seguridad se estableció de forma predeterminada.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si un mecanismo predeterminado, en lugar del proveedor original del descriptor de seguridad, proporciona el SID propietario del descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

Para establecer esta marca, utilice el [CSecurityDesc::SetOwner](#setowner) método.

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Determina si la lista de control de acceso del sistema (SACL) está configurada para admitir la propagación automática.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL que está configurada para admitir la propagación automática de entradas de control de acceso (ACE) heredables a objetos secundarios existentes. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Determina si el descriptor de seguridad está configurado con una lista de control de acceso (SACL) predeterminada del sistema.

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL predeterminada, false en caso contrario.

### <a name="remarks"></a>Observaciones

Este indicador puede afectar a cómo el sistema trata la SACL, con respecto a la herencia de entrada de control de acceso (ACE). El sistema ignora esta marca si no se establece el indicador SE_SACL_PRESENT.

Para establecer esta marca, utilice el [CSecurityDesc::SetSacl](#setsacl) método.

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Determina si el descriptor de seguridad contiene una lista de control de acceso del sistema (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad contiene una SACL, false en caso contrario.

### <a name="remarks"></a>Observaciones

Para establecer esta marca, utilice el [CSecurityDesc::SetSacl](#setsacl) método.

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected

Determina si la lista de control de acceso del sistema (SACL) está configurada para evitar modificaciones.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la SACL está configurada para evitar que las entradas de control de acceso (ACE) heredables modifiquen el descriptor de seguridad. De lo contrario, devuelve un valor falso.

### <a name="remarks"></a>Observaciones

Para establecer esta marca, utilice el [CSecurityDesc::SetSacl](#setsacl) método.

Este método admite la propagación automática de ACE heredables.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Determina si el descriptor de seguridad está en formato autorelativo.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el descriptor de seguridad está en formato autorelativo con toda la información de seguridad de un bloque contiguo de memoria. Devuelve false si el descriptor de seguridad está en formato absoluto. Para obtener más información, vea Descriptores de [seguridad absolutos y autorelativos](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Llame a este método para convertir el descriptor de seguridad al formato absoluto.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de la información en sí. Un descriptor de seguridad en formato autorelativo contiene la información de un bloque contiguo de memoria. En un descriptor de seguridad `SECURITY_DESCRIPTOR` autorelativo, una estructura siempre inicia la información, pero los demás componentes del descriptor de seguridad pueden seguir la estructura en cualquier orden. En lugar de utilizar direcciones de memoria, los componentes del descriptor de seguridad autorelativo se identifican mediante desplazamientos desde el principio del descriptor de seguridad. Este formato es útil cuando un descriptor de seguridad debe almacenarse en un disco o transmitirse mediante un protocolo de comunicaciones. Para obtener más información, vea Descriptores de [seguridad absolutos y autorelativos](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Llame a este método para convertir el descriptor de seguridad a formato autorelativo.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el método se realiza correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de contener la información en sí. Un descriptor de seguridad en formato autorelativo contiene la información de un bloque contiguo de memoria. En un descriptor de seguridad `SECURITY_DESCRIPTOR` autorelativo, una estructura siempre inicia la información, pero los demás componentes del descriptor de seguridad pueden seguir la estructura en cualquier orden. En lugar de utilizar direcciones de memoria, los componentes del descriptor de seguridad se identifican mediante desplazamientos desde el principio del descriptor de seguridad. Este formato es útil cuando un descriptor de seguridad debe almacenarse en un disco o transmitirse mediante un protocolo de comunicaciones. Para obtener más información, vea Descriptores de [seguridad absolutos y autorelativos](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::operador ?

Operador de asignación.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Estructura `SECURITY_DESCRIPTOR` u `CSecurityDesc` objeto que `CSecurityDesc` se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CSecurityDesc` objeto actualizado.

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *

Convierte un valor en un `SECURITY_DESCRIPTOR` puntero a la estructura.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::SetControl

Establece los bits de control de un descriptor de seguridad.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parámetros

*ControlbitsOfInterest*<br/>
Máscara SECURITY_DESCRIPTOR_CONTROL que indica los bits de control que se van a establecer. Para obtener una lista de los indicadores que se pueden establecer, vea [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Una máscara de SECURITY_DESCRIPTOR_CONTROL que indica los nuevos valores para los bits de control especificados por la máscara *ControlBitsOfInterest.* Este parámetro puede ser una combinación de los indicadores enumerados para el *ControlBitsOfInterest* parámetro.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Este método llama a [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl

Establece la información en una lista de control de acceso discrecional (DACL). Si una DACL ya está presente en el descriptor de seguridad, se reemplaza.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Dacl*<br/>
Referencia a `CDacl` un objeto que especifica la DACL para el descriptor de seguridad. Este parámetro no debe ser NULL. Para establecer una DACL NULL en el descriptor de seguridad, la primera forma del método se debe usar con *bPresent* establecido en false.

*bPresente*<br/>
Especifica un indicador que indica la presencia de una DACL en el descriptor de seguridad. Si este parámetro es true, el método `SECURITY_DESCRIPTOR_CONTROL` establece el SE_DACL_PRESENT marca en la estructura y utiliza los valores en el *Dacl* y *bDefaulted* parámetros. Si es false, el método borra el SE_DACL_PRESENT marca y *bDefaulted* se omite.

*bPredeterminado*<br/>
Especifica un indicador que indica el origen de la DACL. Si este indicador es true, la DACL se ha recuperado mediante algún mecanismo predeterminado. Si es false, un usuario ha especificado explícitamente la DACL. El método almacena este valor en `SECURITY_DESCRIPTOR_CONTROL` el SE_DACL_DEFAULTED marca de la estructura. Si no se especifica este parámetro, se borra el indicador de SE_DACL_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Hay una diferencia importante entre una DACL vacía y una DACL inexistente. Cuando una DACL está vacía, no contiene entradas de control de acceso y no se han concedido explícitamente derechos de acceso. Como resultado, el acceso al objeto se deniega implícitamente. Cuando un objeto no tiene DACL, por otro lado, no se asigna ninguna protección al objeto y se concede cualquier solicitud de acceso.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup

Establece la información de grupo principal de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de grupo principal ya presente.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Sid*<br/>
Referencia a un [CSid](../../atl/reference/csid-class.md) objeto para el nuevo grupo principal del descriptor de seguridad. Este parámetro no debe ser NULL. Un descriptor de seguridad se puede marcar como no tener una DACL o una SACL, pero debe tener un grupo y un propietario, incluso estos son el SID NULL (que es un SID integrado con un significado especial).

*bPredeterminado*<br/>
Indica si la información del grupo principal se derivó de un mecanismo predeterminado. Si este valor es true, es información predeterminada y el método `SECURITY_DESCRIPTOR_CONTROL` almacena este valor como el SE_GROUP_DEFAULTED marca en la estructura. Si este parámetro es cero, se borra el indicador SE_GROUP_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

Establece la información de propietario de un descriptor de seguridad de formato absoluto. Reemplaza cualquier información del propietario ya presente.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Sid*<br/>
El [cSid](../../atl/reference/csid-class.md) objeto para el nuevo propietario principal del descriptor de seguridad. Este parámetro no debe ser NULL.

*bPredeterminado*<br/>
Indica si la información del propietario se deriva de un mecanismo predeterminado. Si este valor es true, es información predeterminada. El método almacena este valor como `SECURITY_DESCRIPTOR_CONTROL` el indicador SE_OWNER_DEFAULTED en la estructura. Si este parámetro es cero, se borra el indicador SE_OWNER_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl

Establece la información en una lista de control de acceso (SACL) del sistema. Si una SACL ya está presente en el descriptor de seguridad, se reemplaza.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parámetros

*Sacl*<br/>
Puntero a `CSacl` un objeto que especifica la SACL para el descriptor de seguridad. Este parámetro no debe ser NULL y debe ser un CSacl objeto. A diferencia de las DACL, no hay diferencia entre NULL y una SACL vacía, ya que los objetos SACL no especifican derechos de acceso, solo información de auditoría.

*bPredeterminado*<br/>
Especifica un indicador que indica el origen de la SACL. Si este indicador es true, la SACL se ha recuperado mediante algún mecanismo predeterminado. Si es false, un usuario ha especificado explícitamente la SACL. El método almacena este valor en `SECURITY_DESCRIPTOR_CONTROL` el SE_SACL_DEFAULTED marca de la estructura. Si no se especifica este parámetro, se borra el indicador SE_SACL_DEFAULTED.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

## <a name="csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString

Convierte un descriptor de seguridad en un formato de cadena.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Pstr*<br/>
Puntero a una cadena terminada en null que recibirá el descriptor de [seguridad de formato](/windows/win32/SecAuthZ/security-descriptor-string-format)de cadena .

*si*<br/>
Especifica una combinación de SECURITY_INFORMATION indicadores de bits para indicar los componentes del descriptor de seguridad que se incluirán en la cadena de salida.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Una vez que el descriptor de seguridad está en formato de cadena, se puede almacenar o transmitir más fácilmente. Utilice `CSecurityDesc::FromString` el método para convertir la cadena en un descriptor de seguridad.

El parámetro *si* puede contener los siguientes indicadores SECURITY_INFORMATION:

|Value|Significado|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Incluya al propietario.|
|GROUP_SECURITY_INFORMATION|Incluya el grupo principal.|
|DACL_SECURITY_INFORMATION|Incluya el DACL.|
|SACL_SECURITY_INFORMATION|Incluya la SACL.|

Si la DACL es NULL y el bit de control SE_DACL_PRESENT se establece en el descriptor de seguridad de entrada, se produce un error en el método.

Si la DACL es NULL y el bit de control SE_DACL_PRESENT no se establece en el descriptor de seguridad de entrada, la cadena de descriptor de seguridad resultante no tiene un componente D:. Consulte Formato de [cadena del descriptor](/windows/win32/SecAuthZ/security-descriptor-string-format) de seguridad para obtener más detalles.

Este método llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
