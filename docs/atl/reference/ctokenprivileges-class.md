---
title: Clase CTokenPrivileges | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CTokenPrivileges
- CTokenPrivileges
- ATL.CTokenPrivileges
dev_langs:
- C++
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: 23
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
ms.openlocfilehash: 4d732dbf27c2155ffb98ca59b140d01ea92458e0
ms.lasthandoff: 02/24/2017

---
# <a name="ctokenprivileges-class"></a>Clase CTokenPrivileges
Esta clase es un contenedor para la **TOKEN_PRIVILEGES** estructura.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|El constructor.|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|Agrega uno o más privilegios para la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::Delete](#delete)|Elimina un privilegio de la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::DeleteAll](#deleteall)|Elimina todos los privilegios de la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetCount](#getcount)|Devuelve el número de entradas de privilegios en el `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Recupera nombres para mostrar los privilegios incluidos en el `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetLength](#getlength)|Devuelve el tamaño del búfer de bytes necesarios para contener el **TOKEN_PRIVILEGES** estructura representado por la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Recupera los identificadores local únicos (LUID) y los indicadores de atributo de la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Recupera los nombres de privilegios y los indicadores de atributo de la `CTokenPrivileges` objeto.|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Devuelve un puntero a la **TOKEN_PRIVILEGES** estructura.|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Recupera el atributo asociado con el nombre de un privilegio determinado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Convierte un valor a un puntero a la **TOKEN_PRIVILEGES** estructura.|  
|[CTokenPrivileges::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Un [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows NT o Windows 2000.  
  
 El token de acceso se utiliza para describir los diversos privilegios de seguridad concedidos a cada usuario. Un privilegio consta de un número de 64 bits denominado identificador local único ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) y una cadena de descriptor.  
  
 El `CTokenPrivileges` clase es un contenedor para la [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura y contiene 0 o más privilegios. Privilegios pueden agregarse, eliminado o consultado mediante los métodos de clase proporcionada.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="a-nameadda--ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Add  
 Agrega uno o más privilegios para la `CTokenPrivileges` objeto de token de acceso.  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrivilege`  
 Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H.  
  
 `bEnable`  
 Si es true, se habilita el privilegio. Si es false, se deshabilita el privilegio.  
  
 `rPrivileges`  
 Hacer referencia a un [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura. Los privilegios y los atributos se copian de esta estructura y se agregan a la `CTokenPrivileges` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera forma de este método devuelve true si los privilegios se han agregado correctamente, false en caso contrario.  
  
##  <a name="a-namectokenprivilegesa--ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges  
 El constructor.  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 La `CTokenPrivileges` objeto que se va a asignar al nuevo objeto.  
  
 `rPrivileges`  
 El [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura para asignar a la nueva `CTokenPrivileges` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CTokenPrivileges` , opcionalmente, se puede crear el objeto con un **TOKEN_PRIVILEGES** estructura o definido anteriormente `CTokenPrivileges` objeto.  
  
##  <a name="a-namedtora--ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges  
 Destructor.  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera todos los recursos asignados.  
  
##  <a name="a-namedeletea--ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete  
 Elimina un privilegio de la `CTokenPrivileges` objeto de token de acceso.  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrivilege`  
 Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H. Por ejemplo, puede especificar este parámetro la constante SE_SECURITY_NAME o su cadena correspondiente, "SeSecurityPrivilege".  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si se ha eliminado correctamente el privilegio.  
  
### <a name="remarks"></a>Comentarios  
 Este método resulta útil como una herramienta para crear tokens restringidos en Windows 2000.  
  
##  <a name="a-namedeletealla--ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll  
 Elimina todos los privilegios de la `CTokenPrivileges` objeto de token de acceso.  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Elimina todos los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso.  
  
##  <a name="a-namegetdisplaynamesa--ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames  
 Recupera nombres para mostrar los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso.  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisplayNames`  
 Puntero a una matriz de objetos `CString`. **CNAME** se define como un typedef: **CTokenPrivileges::CAtlArray\<CString >**.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pDisplayNames` es un puntero a una matriz de `CString` objetos que recibirán los nombres para mostrar correspondientes a los privilegios incluidos en el `CTokenPrivileges` objeto. Este método recupera los nombres para mostrar solo para los privilegios especificados en la sección privilegios definidos de WINNT. H.  
  
 Este método recupera un nombre que se pueda mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre que se pueden mostrar es "Forzar el apagado desde un sistema remoto". Para obtener el nombre del sistema, use [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).  
  
##  <a name="a-namegetcounta--ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount  
 Devuelve el número de entradas de privilegios en el `CTokenPrivileges` objeto.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de privilegios incluidos en el `CTokenPrivileges` objeto.  
  
##  <a name="a-namegetlengtha--ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength  
 Devuelve la longitud de la `CTokenPrivileges` objeto.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de bytes necesarios para contener una **TOKEN_PRIVILEGES** estructura representado por la `CTokenPrivileges` objeto, incluidas todas las entradas de privilegio que contiene.  
  
##  <a name="a-namegetluidsandattributesa--ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes  
 Recupera los identificadores local únicos (LUID) y los indicadores de atributo de la `CTokenPrivileges` objeto.  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPrivileges`  
 Puntero a una matriz de [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) objetos. **CLUIDArray** es una definición de tipo se define como **CAtlArray\<LUID > CLUIDArray**.  
  
 `pAttributes`  
 Puntero a una matriz de objetos DWORD. Si este parámetro se omite o NULL, no se recuperan los atributos. **CAttributes** es una definición de tipo se define como **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Comentarios  
 Este método enumerará todos los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso y coloque el LUID individuales y (opcionalmente) los marcadores de atributo en objetos de la matriz.  
  
##  <a name="a-namegetnamesandattributesa--ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes  
 Recupera los atributos name y los indicadores de la `CTokenPrivileges` objeto.  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNames*  
 Puntero a una matriz de `CString` objetos. **CNAME** es una definición de tipo se define como **CAtlArray \<CString > CNAME**.  
  
 `pAttributes`  
 Puntero a una matriz de objetos DWORD. Si este parámetro se omite o NULL, no se recuperan los atributos. **CAttributes** es una definición de tipo se define como **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Comentarios  
 Este método enumerará todos los privilegios incluidos en el `CTokenPrivileges` objeto, colocar el nombre y (opcionalmente) los marcadores de atributo en objetos de la matriz.  
  
 Este método recupera el nombre de atributo, en lugar de en el nombre que se pueda mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre del sistema es "SeRemoteShutdownPrivilege." Para obtener el nombre que se pueden mostrar, use el método [CTokenPrivileges::GetDisplayNames](#getdisplaynames).  
  
##  <a name="a-namegetptokenprivilegesa--ctokenprivilegesgetptokenprivileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 Devuelve un puntero a la **TOKEN_PRIVILEGES** estructura.  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura.  
  
##  <a name="a-namelookupprivilegea--ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege  
 Recupera el atributo asociado con el nombre de un privilegio determinado.  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrivilege`  
 Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H. Por ejemplo, puede especificar este parámetro la constante SE_SECURITY_NAME o su cadena correspondiente, "SeSecurityPrivilege".  
  
 `pdwAttributes`  
 Puntero a una variable que recibe los atributos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el atributo es recuperado correctamente.  
  
##  <a name="a-nameoperatoreqa--ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::operator =  
 Operador de asignación.  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rPrivileges`  
 El [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura para asignar a la `CTokenPrivileges` objeto.  
  
 `rhs`  
 La `CTokenPrivileges` objeto que se va a asignar al objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CTokenPrivileges` objeto.  
  
##  <a name="a-nameoperatorconsttokenprivilegesstara--ctokenprivilegesoperator-const-tokenprivileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 Convierte un valor a un puntero a la **TOKEN_PRIVILEGES** estructura.  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>Comentarios  
 Convierte un valor a un puntero a la [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) estructura.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)

