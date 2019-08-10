---
title: Clase CTokenPrivileges
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: 5f8379d20d8c8d525cd645e1d4aa0c751e16f531
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915532"
---
# <a name="ctokenprivileges-class"></a>Clase CTokenPrivileges

Esta clase es un contenedor para la `TOKEN_PRIVILEGES` estructura.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CTokenPrivileges
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|El constructor.|
|[CTokenPrivileges::~CTokenPrivileges](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|Agrega uno o más privilegios al `CTokenPrivileges` objeto.|
|[CTokenPrivileges::Delete](#delete)|Elimina un privilegio del `CTokenPrivileges` objeto.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Elimina todos los privilegios del `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetCount](#getcount)|Devuelve el número de entradas de privilegios en `CTokenPrivileges` el objeto.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Recupera los nombres para mostrar de los privilegios contenidos en `CTokenPrivileges` el objeto.|
|[CTokenPrivileges::GetLength](#getlength)|Devuelve el tamaño de búfer en bytes necesario para contener `TOKEN_PRIVILEGES` la estructura representada por el `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Recupera los identificadores únicos locales (LUID) y las `CTokenPrivileges` marcas de atributo del objeto.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Recupera los nombres de los privilegios y las marcas de `CTokenPrivileges` atributo del objeto.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Devuelve un puntero a la `TOKEN_PRIVILEGES` estructura.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Recupera el atributo asociado a un nombre de privilegio determinado.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenPrivileges:: Operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Convierte un valor en un puntero a la `TOKEN_PRIVILEGES` estructura.|
|[CTokenPrivileges::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/desktop/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

El token de acceso se utiliza para describir los distintos privilegios de seguridad concedidos a cada usuario. Un privilegio consta de un número de 64 bits denominado identificador local único ( [LUID](/windows/desktop/api/winnt/ns-winnt-luid)) y una cadena de descriptor.

La `CTokenPrivileges` clase es un contenedor para la estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) y contiene 0 o más privilegios. Los privilegios se pueden agregar, eliminar o consultar mediante los métodos de clase proporcionados.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/desktop/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="add"></a>  CTokenPrivileges::Add

Agrega uno o más privilegios al `CTokenPrivileges` objeto de token de acceso.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal y como se define en WINNt. Archivo de encabezado H.

*bEnable*<br/>
Si es true, el privilegio está habilitado. Si es false, el privilegio está deshabilitado.

*rPrivileges*<br/>
Referencia a una estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) . Los privilegios y atributos se copian de esta estructura y se agregan al `CTokenPrivileges` objeto.

### <a name="return-value"></a>Valor devuelto

La primera forma de este método devuelve true si los privilegios se han agregado correctamente; de lo contrario, es false.

##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges

El constructor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`CTokenPrivileges` Objeto que se va a asignar al nuevo objeto.

*rPrivileges*<br/>
Estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) que se va a asignar al `CTokenPrivileges` nuevo objeto.

### <a name="remarks"></a>Comentarios

El `CTokenPrivileges` objeto se puede crear opcionalmente mediante una `TOKEN_PRIVILEGES` estructura o un objeto definido `CTokenPrivileges` previamente.

##  <a name="dtor"></a>  CTokenPrivileges::~CTokenPrivileges

Destructor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados.

##  <a name="delete"></a>  CTokenPrivileges::Delete

Elimina un privilegio del objeto de `CTokenPrivileges` token de acceso.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal y como se define en WINNt. Archivo de encabezado H. Por ejemplo, este parámetro puede especificar la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege".

### <a name="return-value"></a>Valor devuelto

Devuelve true si el privilegio se eliminó correctamente; de lo contrario, false.

### <a name="remarks"></a>Comentarios

Este método es útil como herramienta para crear tokens restringidos.

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

Elimina todos los privilegios del objeto `CTokenPrivileges` de token de acceso.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Comentarios

Elimina todos los privilegios contenidos en el `CTokenPrivileges` objeto de token de acceso.

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

Recupera los nombres para mostrar de los privilegios contenidos en `CTokenPrivileges` el objeto de token de acceso.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDisplayNames*<br/>
Puntero a una matriz de objetos `CString`. `CNames`se define como una definición de `CTokenPrivileges::CAtlArray<CString>`tipo:.

### <a name="remarks"></a>Comentarios

El parámetro `pDisplayNames` es un puntero a una matriz de `CString` objetos que recibirá los nombres para mostrar correspondientes a los privilegios contenidos en `CTokenPrivileges` el objeto. Este método solo recupera los nombres para mostrar de los privilegios especificados en la sección privilegios definidos de WINNt. C.

Este método recupera un nombre que se pueda mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre que se pueda mostrar es "forzar cierre desde un sistema remoto". Para obtener el nombre del sistema, use [CTokenPrivileges:: GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

Devuelve el número de entradas de privilegios en `CTokenPrivileges` el objeto.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de privilegios contenidos en el `CTokenPrivileges` objeto.

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

Devuelve la longitud del `CTokenPrivileges` objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes necesarios para contener una `TOKEN_PRIVILEGES` estructura representada `CTokenPrivileges` por el objeto, incluidas todas las entradas de privilegios que contiene.

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

Recupera los identificadores únicos locales (LUID) y las `CTokenPrivileges` marcas de atributo del objeto.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*<br/>
Puntero a una matriz de objetos [LUID](/windows/desktop/api/winnt/ns-winnt-luid) . `CLUIDArray`es un typedef definido como `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Puntero a una matriz de objetos DWORD. Si este parámetro se omite o es NULL, no se recuperan los atributos. `CAttributes`es un typedef definido como `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los privilegios contenidos en el `CTokenPrivileges` objeto de token de acceso y colocará el LUID individual y, opcionalmente, las marcas de atributo en los objetos de matriz.

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

Recupera las marcas de nombre y atributo del `CTokenPrivileges` objeto.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pNames*<br/>
Puntero a una matriz de `CString` objetos. `CNames`es un typedef definido como `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Puntero a una matriz de objetos DWORD. Si este parámetro se omite o es NULL, no se recuperan los atributos. `CAttributes`es un typedef definido como `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los privilegios contenidos en el `CTokenPrivileges` objeto, colocando el nombre y, opcionalmente, las marcas de atributo en objetos de matriz.

Este método recupera el nombre del atributo, en lugar del nombre que se pueda mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre del sistema es "SeRemoteShutdownPrivilege". Para obtener el nombre que se pueda mostrar, use el método [CTokenPrivileges:: GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

Devuelve un puntero a la `TOKEN_PRIVILEGES` estructura.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) .

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

Recupera el atributo asociado a un nombre de privilegio determinado.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal y como se define en WINNt. Archivo de encabezado H. Por ejemplo, este parámetro puede especificar la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege".

*pdwAttributes*<br/>
Puntero a una variable que recibe los atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el atributo se recupera correctamente; en caso contrario, false.

##  <a name="operator_eq"></a>CTokenPrivileges:: Operator =

Operador de asignación.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
Estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) que se va a asignar `CTokenPrivileges` al objeto.

*rhs*<br/>
`CTokenPrivileges` Objeto que se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CTokenPrivileges` actualizado.

##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges:: Operator const TOKEN_PRIVILEGES\*

Convierte un valor en un puntero a la `TOKEN_PRIVILEGES` estructura.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Convierte un valor en un puntero a la estructura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) .

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
