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
ms.openlocfilehash: ceb9aeca6b99e7fc9d08625e11cbdb182fb3dc9e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330540"
---
# <a name="ctokenprivileges-class"></a>Clase CTokenPrivileges

Esta clase es un `TOKEN_PRIVILEGES` contenedor para la estructura.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CTokenPrivileges
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|El constructor.|
|[CTokenPrivileges::-CTokenPrivileges](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|Agrega uno o más `CTokenPrivileges` privilegios al objeto.|
|[CTokenPrivileges::Delete](#delete)|Elimina un privilegio `CTokenPrivileges` del objeto.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Elimina todos los `CTokenPrivileges` privilegios del objeto.|
|[CTokenPrivileges::GetCount](#getcount)|Devuelve el número de entradas `CTokenPrivileges` de privilegios en el objeto.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Recupera los nombres para mostrar de `CTokenPrivileges` los privilegios contenidos en el objeto.|
|[CTokenPrivileges::GetLength](#getlength)|Devuelve el tamaño del búfer `TOKEN_PRIVILEGES` en bytes necesarios para contener la estructura representada por el `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Recupera los identificadores únicos locales (LUID) `CTokenPrivileges` y las marcas de atributo del objeto.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Recupera los nombres de privilegio `CTokenPrivileges` y las marcas de atributo del objeto.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Devuelve un puntero `TOKEN_PRIVILEGES` a la estructura.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Recupera el atributo asociado a un nombre de privilegio determinado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Convierte un valor en un `TOKEN_PRIVILEGES` puntero a la estructura.|
|[CTokenPrivileges::operator ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

Un token de [acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

El token de acceso se utiliza para describir los diversos privilegios de seguridad concedidos a cada usuario. Un privilegio consta de un número de 64 bits denominado identificador único local ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) y una cadena de descriptor.

La `CTokenPrivileges` clase es un contenedor para la estructura [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) y contiene 0 o más privilegios. Los privilegios se pueden agregar, eliminar o consultar mediante los métodos de clase proporcionados.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Add

Agrega uno o varios `CTokenPrivileges` privilegios al objeto de token de acceso.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en winNT. Archivo de encabezado H.

*bHabilitar*<br/>
Si es true, el privilegio está habilitado. Si es false, el privilegio está deshabilitado.

*rPrivileges*<br/>
Referencia a una estructura [TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges) Los privilegios y atributos se copian `CTokenPrivileges` de esta estructura y se agregan al objeto.

### <a name="return-value"></a>Valor devuelto

La primera forma de este método devuelve true si los privilegios se agregan correctamente, false en caso contrario.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

El constructor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CTokenPrivileges` que se va a asignar al nuevo objeto.

*rPrivileges*<br/>
La [estructura TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) que `CTokenPrivileges` se va a asignar al nuevo objeto.

### <a name="remarks"></a>Observaciones

El `CTokenPrivileges` objeto se puede crear `TOKEN_PRIVILEGES` opcionalmente utilizando una estructura o un objeto definido `CTokenPrivileges` previamente.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges::-CTokenPrivileges

Destructor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos asignados.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete

Elimina un privilegio `CTokenPrivileges` del objeto de token de acceso.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en winNT. Archivo de encabezado H. Por ejemplo, este parámetro podría especificar la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege."

### <a name="return-value"></a>Valor devuelto

Devuelve true si el privilegio se eliminó correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

Este método es útil como herramienta para crear tokens restringidos.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll

Elimina todos los `CTokenPrivileges` privilegios del objeto de token de acceso.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Observaciones

Elimina todos los privilegios `CTokenPrivileges` contenidos en el objeto de token de acceso.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Recupera los nombres para mostrar de `CTokenPrivileges` los privilegios contenidos en el objeto de token de acceso.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDisplayNames*<br/>
Puntero a una matriz de objetos `CString`. `CNames`se define como typedef: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Observaciones

El `pDisplayNames` parámetro es un puntero `CString` a una matriz de objetos que recibirá `CTokenPrivileges` los nombres para mostrar correspondientes a los privilegios contenidos en el objeto. Este método recupera nombres para mostrar solo para los privilegios especificados en la sección Privilegios definidos de WINNT. H.

Este método recupera un nombre que se puede mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre que se puede mostrar es "Forzar apagado desde un sistema remoto." Para obtener el nombre del sistema, utilice [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount

Devuelve el número de entradas `CTokenPrivileges` de privilegios en el objeto.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de privilegios contenidos en el `CTokenPrivileges` objeto.

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength

Devuelve la longitud `CTokenPrivileges` del objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes `TOKEN_PRIVILEGES` necesarios para `CTokenPrivileges` contener una estructura representada por el objeto, incluidas todas las entradas de privilegios que contiene.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Recupera los identificadores únicos locales (LUID) `CTokenPrivileges` y las marcas de atributo del objeto.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*<br/>
Puntero a una matriz de objetos [LUID.](/windows/win32/api/winnt/ns-winnt-luid) `CLUIDArray`es una definición `CAtlArray<LUID> CLUIDArray`de tipo definida como .

*pAtributos*<br/>
Puntero a una matriz de objetos DWORD. Si se omite este parámetro o NULL, no se recuperan los atributos. `CAttributes`es una definición `CAtlArray <DWORD> CAttributes`de tipo definida como .

### <a name="remarks"></a>Observaciones

Este método enumerará todos los privilegios `CTokenPrivileges` contenidos en el objeto de token de acceso y colocará los LUID individuales y (opcionalmente) los indicadores de atributo en objetos de matriz.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Recupera las marcas de nombre `CTokenPrivileges` y atributo del objeto.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pNombres*<br/>
Puntero a una `CString` matriz de objetos. `CNames`es una definición `CAtlArray <CString> CNames`de tipo definida como .

*pAtributos*<br/>
Puntero a una matriz de objetos DWORD. Si se omite este parámetro o NULL, no se recuperan los atributos. `CAttributes`es una definición `CAtlArray <DWORD> CAttributes`de tipo definida como .

### <a name="remarks"></a>Observaciones

Este método enumerará todos los privilegios `CTokenPrivileges` contenidos en el objeto, colocando el nombre y (opcionalmente) los indicadores de atributo en objetos de matriz.

Este método recupera el nombre del atributo, en lugar del nombre que se puede mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre del sistema es "SeRemoteShutdownPrivilege." Para obtener el nombre que se puede mostrar, utilice el método [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Devuelve un puntero `TOKEN_PRIVILEGES` a la estructura.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [estructura TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege

Recupera el atributo asociado a un nombre de privilegio determinado.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en winNT. Archivo de encabezado H. Por ejemplo, este parámetro podría especificar la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege."

*pdwAttributes*<br/>
Puntero a una variable que recibe los atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el atributo se recupera correctamente, false en caso contrario.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::operator ?

Operador de asignación.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
La [estructura TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) que `CTokenPrivileges` se va a asignar al objeto.

*rhs*<br/>
Objeto `CTokenPrivileges` que se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CTokenPrivileges` objeto actualizado.

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES\*

Convierte un valor en un `TOKEN_PRIVILEGES` puntero a la estructura.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Observaciones

Convierte un valor en un puntero a la [estructura TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
