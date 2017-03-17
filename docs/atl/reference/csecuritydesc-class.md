---
title: Clase CSecurityDesc | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6dbd586ee3ee07d3c567fa0aae46446397dfb62b
ms.lasthandoff: 02/24/2017

---
# <a name="csecuritydesc-class"></a>Clase CSecurityDesc
Esta clase es un contenedor para la **SECURITY_DESCRIPTOR** estructura.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CSecurityDesc
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|El constructor.|  
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::FromString](#fromstring)|Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad válida y funcional.|  
|[CSecurityDesc::GetControl](#getcontrol)|Recupera la información del descriptor de seguridad de control.|  
|[CSecurityDesc::GetDacl](#getdacl)|Recupera información de control de acceso discrecional (DACL) de la lista del descriptor de seguridad.|  
|[CSecurityDesc::GetGroup](#getgroup)|Recupera la información del grupo principal del descriptor de seguridad.|  
|[CSecurityDesc::GetOwner](#getowner)|Recupera información de propietario del descriptor de seguridad.|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Devuelve un puntero a la **SECURITY_DESCRIPTOR** estructura.|  
|[CSecurityDesc::GetSacl](#getsacl)|Recupera información del sistema de control de acceso (SACL) de la lista del descriptor de seguridad.|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Determina si la DACL está configurada para admitir la propagación automática.|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Determina si el descriptor de seguridad está configurado con una DACL predeterminada.|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Determina si el descriptor de seguridad contiene una DACL.|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Determina si la DACL está configurada para evitar modificaciones.|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Determina si el identificador de seguridad de grupo del descriptor de seguridad (SID) se ha establecido de forma predeterminada.|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Determina si el SID de propietario del descriptor de seguridad se ha establecido de forma predeterminada.|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Determina si la SACL está configurada para admitir la propagación automática.|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Determina si el descriptor de seguridad está configurado con un SACL predeterminado.|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Determina si el descriptor de seguridad contiene una SACL.|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Determina si la SACL está configurada para impedir modificaciones.|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Determina si el descriptor de seguridad está en formato autorelativo.|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Llamar a este método para convertir el descriptor de seguridad en formato absoluto.|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Llame a este método para convertir el descriptor de seguridad a formato autorelativo.|  
|[CSecurityDesc::SetControl](#setcontrol)|Establece los bits de control de un descriptor de seguridad.|  
|[CSecurityDesc::SetDacl](#setdacl)|Establece la información en una DACL. Si ya hay una DACL del descriptor de seguridad, se reemplaza.|  
|[CSecurityDesc::SetGroup](#setgroup)|Establece la información de grupo principal de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de grupos primarios ya está presente.|  
|[CSecurityDesc::SetOwner](#setowner)|Establece la información de propietario del descriptor de seguridad de un formato absoluto, reemplazando cualquier información de propietario ya está presente.|  
|[CSecurityDesc::SetSacl](#setsacl)|Establece la información en una SACL. Si ya hay una SACL del descriptor de seguridad, se reemplaza.|  
|[CSecurityDesc::ToString](#tostring)|Convierte un descriptor de seguridad en un formato de cadena.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Devuelve un puntero a la **SECURITY_DESCRIPTOR** estructura.|  
|[CSecurityDesc::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 El **SECURITY_DESCRIPTOR** estructura contiene la información de seguridad asociada a un objeto. Aplicaciones utilizan esta estructura para establecer y consultar el estado de seguridad de un objeto. Consulte también [AtlGetSecurityDescriptor](http://msdn.microsoft.com/library/233578b8-dcc5-4f51-8e62-7cdcc2ff6b11).  
  
 Las aplicaciones no deben modificar el **SECURITY_DESCRIPTOR** estructura directamente y en su lugar, debería utilizar los métodos de clase proporcionados.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 El constructor.  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `CSecurityDesc` objeto o **SECURITY_DESCRIPTOR** estructura para asignar a la nueva `CSecurityDesc` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CSecurityDesc` , opcionalmente, se puede crear el objeto con un **SECURITY_DESCRIPTOR** estructura o definido anteriormente `CSecurityDesc` objeto.  
  
##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 Destructor.  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera todos los recursos asignados.  
  
##  <a name="fromstring"></a>CSecurityDesc::FromString  
 Convierte un descriptor de seguridad de formato de cadena en un descriptor de seguridad válida y funcional.  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstr`  
 Puntero a una cadena terminada en null que contiene el [descriptor de seguridad de formato de cadena](http://msdn.microsoft.com/library/windows/desktop/aa379570) a convertirse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si se ejecuta correctamente. Produce una excepción en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 La cadena puede crearse mediante [CSecurityDesc::ToString](#tostring). Convertir el descriptor de seguridad en una cadena facilita almacenar y transmitir.  
  
 Este método solo está disponible con Windows 2000 y versiones posteriores porque llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
##  <a name="getcontrol"></a>CSecurityDesc::GetControl  
 Recupera la información del descriptor de seguridad de control.  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *psdc*  
 Puntero a un **SECURITY_DESCRIPTOR_CONTROL** estructura que recibe información de control del descriptor de seguridad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método tiene éxito, false si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Este método sólo es relevante si utiliza Windows 2000 o posterior, ya que llama a [GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647).  
  
##  <a name="getdacl"></a>CSecurityDesc::GetDacl  
 Recupera información de control de acceso discrecional (DACL) de la lista del descriptor de seguridad.  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDacl`  
 Puntero a un `CDacl` estructura en la que almacenar una copia de la DACL del descriptor de seguridad. Si un discrecional **ACL** existe, el método establece `pDacl` para la dirección de la seguridad del discrecional descriptor **ACL**. Si un discrecional **ACL** no existe ningún valor se almacena.  
  
 `pbPresent`  
 Puntero a un valor que indica la presencia de un discrecional **ACL** en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene un discrecional **ACL**, este parámetro se establece en true. Si el descriptor de seguridad no contiene un discrecional **ACL**, este parámetro se establece en false.  
  
 `pbDefaulted`  
 Puntero a un indicador se establece en el valor de la marca SE_DACL_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura si un discrecional **ACL** existe para el descriptor de seguridad. Si es true, esta marca el discrecional **ACL** recuperada por un mecanismo predeterminado; si es false, el discrecional **ACL** especificó explícitamente por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método tiene éxito, false si se produce un error.  
  
##  <a name="getgroup"></a>CSecurityDesc::GetGroup  
 Recupera la información del grupo principal del descriptor de seguridad.  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en el CDacl.  
  
 `pbDefaulted`  
 Puntero a un indicador se establece en el valor de la marca SE_GROUP_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura cuando el método devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método tiene éxito, false si se produce un error.  
  
##  <a name="getowner"></a>CSecurityDesc::GetOwner  
 Recupera información de propietario del descriptor de seguridad.  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid](../../atl/reference/csid-class.md) (identificador de seguridad) que recibe una copia del grupo almacenado en el CDacl.  
  
 `pbDefaulted`  
 Puntero a un indicador se establece en el valor de la marca SE_OWNER_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura cuando el método devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método tiene éxito, false si se produce un error.  
  
##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 Devuelve un puntero a la **SECURITY_DESCRIPTOR** estructura.  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) estructura.  
  
##  <a name="getsacl"></a>CSecurityDesc::GetSacl  
 Recupera información del sistema de control de acceso (SACL) de la lista del descriptor de seguridad.  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSacl`  
 Puntero a un `CSacl` estructura en la que almacenar una copia de la SACL del descriptor de seguridad. Si un sistema **ACL** existe, el método establece `pSacl` a la dirección del sistema del descriptor de seguridad **ACL**. Si un sistema **ACL** no existe ningún valor se almacena.  
  
 `pbPresent`  
 Puntero a un indicador que establece el método para indicar la presencia de un sistema **ACL** en el descriptor de seguridad especificado. Si el descriptor de seguridad contiene un sistema **ACL**, este parámetro se establece en true. Si el descriptor de seguridad no contiene un sistema **ACL**, este parámetro se establece en false.  
  
 `pbDefaulted`  
 Puntero a un indicador se establece en el valor de la marca SE_SACL_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura si un sistema **ACL** existe para el descriptor de seguridad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método tiene éxito, false si se produce un error.  
  
##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 Determina si la lista de control de acceso discrecional (DACL) está configurada para admitir la propagación automática.  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una DACL que se configura para admitir la propagación automática de entradas de control de acceso heredables (ACE) a los objetos secundarios existentes. De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.  
  
##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 Determina si el descriptor de seguridad se configura con una lista de control de acceso discrecional (DACL) de forma predeterminada.  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una DACL, de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Este indicador puede afectar a cómo el sistema trata la DACL con respecto a la herencia de control de acceso (ACE) de entrada. Por ejemplo, si el creador de un objeto no especifica una DACL, el objeto recibe la DACL del token de acceso del creador. El sistema omite esta marca si no se establece la marca SE_DACL_PRESENT.  
  
 Este indicador se utiliza para determinar cómo se calcula la DACL final en el objeto y no se almacena físicamente en el control de descriptor de seguridad del objeto protegible.  
  
 Para establecer esta marca, utilice la [CSecurityDesc::SetDacl](#setdacl) método.  
  
##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 Determina si el descriptor de seguridad contiene una lista de control de acceso discrecional (DACL).  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una DACL.  
  
### <a name="remarks"></a>Comentarios  
 Si no se establece este indicador, o si se establece esta marca y la DACL es NULL, el descriptor de seguridad permite el acceso completo a todos los usuarios.  
  
 Este indicador se utiliza para almacenar la información de seguridad especificada por el autor de la llamada hasta que el descriptor de seguridad está asociado a un objeto protegible. Una vez que el descriptor de seguridad está asociado a un objeto protegible, el indicador SE_DACL_PRESENT siempre se establece en el control de descriptor de seguridad.  
  
 Para establecer esta marca, utilice la [CSecurityDesc::SetDacl](#setdacl) método.  
  
##  <a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected  
 Determina si la lista de control de acceso discrecional (DACL) está configurada para impedir modificaciones.  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la DACL está configurada para evitar que el descriptor de seguridad está modificando las entradas de control de acceso heredables (ACE). De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer esta marca, utilice la [CSecurityDesc::SetDacl](#setdacl) método.  
  
 Este método sólo es significativo para Windows 2000 o posterior, ya que sólo Windows 2000 admite la propagación automática de las ACE heredables.  
  
##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 Determina si el identificador de seguridad de grupo del descriptor de seguridad (SID) se ha establecido de forma predeterminada.  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad no proporciona un mecanismo de forma predeterminada, en lugar de proveedor original del descriptor de seguridad, SID de grupo. De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer esta marca, utilice la [CSecurityDesc::SetGroup](#setgroup) método.  
  
##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 Determina si el identificador de seguridad de propietario del descriptor de seguridad (SID) se ha establecido de forma predeterminada.  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si no proporciona un mecanismo de forma predeterminada, en lugar de proveedor original del descriptor de seguridad, SID de propietario del descriptor de seguridad. De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer esta marca, utilice la [CSecurityDesc::SetOwner](#setowner) método.  
  
##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 Determina si la lista de control de acceso de sistema (SACL) está configurada para admitir la propagación automática.  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una SACL que se configura para admitir la propagación automática de entradas de control de acceso heredables (ACE) a los objetos secundarios existentes. De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 El sistema establece este bit cuando realiza el algoritmo de herencia automática para el objeto y sus objetos secundarios existentes.  
  
##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 Determina si el descriptor de seguridad se configura con una lista de control de acceso del sistema predeterminada (SACL).  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una SACL, de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Este indicador puede afectar a cómo el sistema trata la SACL, con respecto a la herencia de control de acceso (ACE) de entrada. El sistema omite esta marca si no se establece la marca SE_SACL_PRESENT.  
  
 Para establecer esta marca, utilice la [CSecurityDesc::SetSacl](#setsacl) método.  
  
##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 Determina si el descriptor de seguridad contiene una lista de control de acceso de sistema (SACL).  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad contiene una SACL.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer esta marca, utilice la [CSecurityDesc::SetSacl](#setsacl) método.  
  
##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 Determina si la lista de control de acceso de sistema (SACL) está configurada para impedir modificaciones.  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la SACL está configurada para impedir que el descriptor de seguridad que se modifican con entradas de control de acceso heredables (ACE). De lo contrario, devuelve un valor falso.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer esta marca, utilice la [CSecurityDesc::SetSacl](#setsacl) método.  
  
 Este método sólo es significativo para Windows 2000 o posterior, ya que sólo Windows 2000 admite la propagación automática de las ACE heredables.  
  
##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 Determina si el descriptor de seguridad está en formato autorelativo.  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el descriptor de seguridad está en formato autorelativo con toda la información de seguridad en un bloque de memoria contiguo. Devuelve false si el descriptor de seguridad está en formato absoluto. Para obtener más información, consulte [absoluto y descriptores de seguridad de Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 Llamar a este método para convertir el descriptor de seguridad en formato absoluto.  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método se produce y false en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de la propia información. Un descriptor de seguridad en formato autorelativo contiene la información en un bloque de memoria contiguo. En un descriptor de seguridad autorelativo un **SECURITY_DESCRIPTOR** siempre inicia la estructura de la información, pero el descriptor de seguridad de otros componentes pueden seguir la estructura en cualquier orden. En lugar de utilizar direcciones de memoria, se identifican los componentes del descriptor de seguridad autorelativo por desplazamientos desde el principio del descriptor de seguridad. Este formato es útil cuando un descriptor de seguridad se guarda en un disco o transmitido a través de un protocolo de comunicaciones. Para obtener más información, consulte [absoluto y descriptores de seguridad de Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 Llame a este método para convertir el descriptor de seguridad a formato autorelativo.  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el método se produce y false en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Un descriptor de seguridad en formato absoluto contiene punteros a la información que contiene, en lugar de que contiene la información en Sí. Un descriptor de seguridad en formato autorelativo contiene la información en un bloque de memoria contiguo. En un descriptor de seguridad autorelativo un **SECURITY_DESCRIPTOR** siempre inicia la estructura de la información, pero el descriptor de seguridad de otros componentes pueden seguir la estructura en cualquier orden. En lugar de utilizar direcciones de memoria, los componentes del descriptor de seguridad se identifican por desplazamientos desde el principio del descriptor de seguridad. Este formato es útil cuando un descriptor de seguridad se guarda en un disco o transmitido a través de un protocolo de comunicaciones. Para obtener más información, consulte [absoluto y descriptores de seguridad de Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="operator_eq"></a>CSecurityDesc::operator =  
 Operador de asignación.  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El **SECURITY_DESCRIPTOR** estructura o `CSecurityDesc` objeto que se va a asignar a la `CSecurityDesc` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CSecurityDesc` objeto.  
  
##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 Convierte un valor a un puntero a la **SECURITY_DESCRIPTOR** estructura.  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="setcontrol"></a>CSecurityDesc::SetControl  
 Establece los bits de control de un descriptor de seguridad.  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ControlBitsOfInterest`  
 Un **SECURITY_DESCRIPTOR_CONTROL** máscara que indica los bits de control para establecer. Para obtener una lista de las marcas que se pueden establecer, consulte [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
 `ControlBitsToSe`t  
 Máscara `SECURITY_DESCRIPTOR_CONTROL` que indica los nuevos valores de los bits de control especificados por la máscara `ControlBitsOfInterest`. Este parámetro puede ser una combinación de las marcas enumeradas para el parámetro `ControlBitsOfInterest`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método está disponible sólo en Windows 2000 y versiones posteriores, ya que llama a [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
##  <a name="setdacl"></a>CSecurityDesc::SetDacl  
 Establece la información en una lista de control de acceso discrecional (DACL). Si ya hay una DACL del descriptor de seguridad, se reemplaza.  
  
```
inline void SetDacl(  
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(  
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *DACL*  
 Hacer referencia a un `CDacl` objeto especificando la DACL para el descriptor de seguridad. Este parámetro no debe ser NULL. Para establecer una DACL NULL en el descriptor de seguridad, el primer formulario del método debe utilizarse con `bPresent` establecido en false.  
  
 `bPresent`  
 Especifica una marca que indica la presencia de una DACL del descriptor de seguridad. Si este parámetro es true, el método establece el indicador SE_DACL_PRESENT la **SECURITY_DESCRIPTOR_CONTROL** estructura y utiliza los valores en el *Dacl* y `bDefaulted` parámetros. Si es false, el método borra el indicador SE_DACL_PRESENT, y `bDefaulted` se omite.  
  
 `bDefaulted`  
 Especifica una marca que indica el origen de la DACL. Si este indicador es true, la DACL se ha recuperado por algún mecanismo de forma predeterminada. Si es false, la DACL se ha especificado explícitamente por el usuario. El método almacena este valor en la marca SE_DACL_DEFAULTED de la **SECURITY_DESCRIPTOR_CONTROL** estructura. Si no se especifica este parámetro, se borra el indicador SE_DACL_DEFAULTED.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Hay una diferencia importante entre una cadena vacía y una DACL que no existe. Cuando una DACL está vacía, no contiene ninguna entrada de control de acceso y derechos de acceso no se haya concedido explícitamente. Como resultado, se deniega implícitamente el acceso al objeto. Cuando un objeto tiene no hay DACL, por otro lado, protección no se asigna al objeto y se concede a cualquier solicitud de acceso.  
  
##  <a name="setgroup"></a>CSecurityDesc::SetGroup  
 Establece la información de grupo principal de un descriptor de seguridad de formato absoluto, reemplazando cualquier información de grupos primarios ya está presente.  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `Sid`  
 Hacer referencia a un [CSid](../../atl/reference/csid-class.md) objeto de grupo principal nueva del descriptor de seguridad. Este parámetro no debe ser NULL. Un descriptor de seguridad puede marcarse como si no tuviera una DACL o una SACL, pero debe tener un grupo y un propietario, incluso éstas son el SID NULL (que es un SID integrado con un significado especial).  
  
 `bDefaulted`  
 Indica si la información del grupo principal se deriva de un mecanismo de forma predeterminada. Si este valor es true, es la información predeterminada y el método almacena este valor como el indicador SE_GROUP_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura. Si este parámetro es cero, se borra el indicador SE_GROUP_DEFAULTED.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="setowner"></a>CSecurityDesc::SetOwner  
 Establece la información de propietario de un descriptor de seguridad de formato absoluto. Reemplaza cualquier información de propietario ya está presente.  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `Sid`  
 El [CSid](../../atl/reference/csid-class.md) objeto para propietario del principal nuevo del descriptor de seguridad. Este parámetro no debe ser NULL.  
  
 `bDefaulted`  
 Indica si la información del propietario se deriva de un mecanismo de forma predeterminada. Si este valor es true, es información de forma predeterminada. El método almacena este valor como el indicador SE_OWNER_DEFAULTED en la **SECURITY_DESCRIPTOR_CONTROL** estructura. Si este parámetro es cero, se borra el indicador SE_OWNER_DEFAULTED.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="setsacl"></a>CSecurityDesc::SetSacl  
 Establece la información en una lista de control de acceso de sistema (SACL). Si ya hay una SACL del descriptor de seguridad, se reemplaza.  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *SACL*  
 Puntero a un `CSacl` objeto especificando la SACL del descriptor de seguridad. Este parámetro no debe ser NULL y debe ser un objeto CSacl. A diferencia de las DACL, no hay ninguna diferencia entre NULL y una SACL vacía, como objetos SACL no especifican los derechos de acceso, sólo información de auditoría.  
  
 `bDefaulted`  
 Especifica una marca que indica el origen de la SACL. Si este indicador es true, la SACL se ha recuperado por algún mecanismo de forma predeterminada. Si es false, la SACL se ha especificado explícitamente por el usuario. El método almacena este valor en la marca SE_SACL_DEFAULTED de la **SECURITY_DESCRIPTOR_CONTROL** estructura. Si no se especifica este parámetro, se borra el indicador SE_SACL_DEFAULTED.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="tostring"></a>CSecurityDesc::ToString  
 Convierte un descriptor de seguridad en un formato de cadena.  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstr`  
 Puntero a una cadena terminada en null que recibirá la [descriptor de seguridad de formato de cadena](http://msdn.microsoft.com/library/windows/desktop/aa379570).  
  
 `si`  
 Especifica una combinación de marcadores de bits SECURITY_INFORMATION para indicar los componentes del descriptor de seguridad para incluir en la cadena de salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Una vez que el descriptor de seguridad está en formato de cadena, más fácilmente se guarda o transmite. Utilice la `CSecurityDesc::FromString` método para convertir la cadena en un descriptor de seguridad.  
  
 El `si` parámetro puede contener los siguientes indicadores SECURITY_INFORMATION:  
  
|Valor|Significado|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|Incluir el propietario.|  
|GROUP_SECURITY_INFORMATION|Incluya el grupo principal.|  
|DACL_SECURITY_INFORMATION|Incluir la DACL.|  
|SACL_SECURITY_INFORMATION|Incluir la SACL.|  
  
 Si la DACL es NULL y el bit de control SE_DACL_PRESENT se establece en el descriptor de seguridad de entrada, el método produce un error.  
  
 Si la DACL es NULL y no se establece el bit de control SE_DACL_PRESENT en el descriptor de seguridad de entrada, la cadena de descriptor de seguridad resultante no tiene un componente D:. Consulte [formato de cadena de Descriptor de seguridad](http://msdn.microsoft.com/library/windows/desktop/aa379570) para obtener más detalles.  
  
 Este método solo está disponible con Windows 2000 y versiones posteriores, ya que llama a [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)

