---
title: CTokenPrivileges (clase)
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
ms.openlocfilehash: 8bca3e1d45d0a85d1d4ceac4ffdf7b11091020f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277310"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges (clase)

Esta clase es un contenedor para el `TOKEN_PRIVILEGES` estructura.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CTokenPrivileges
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|El constructor.|
|[CTokenPrivileges::~CTokenPrivileges](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|Agrega uno o más privilegios para la `CTokenPrivileges` objeto.|
|[CTokenPrivileges::Delete](#delete)|Elimina un privilegio de la `CTokenPrivileges` objeto.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Elimina todos los privilegios de la `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetCount](#getcount)|Devuelve el número de entradas de privilegios en el `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Recupera nombres para mostrar los privilegios incluidos en el `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetLength](#getlength)|Devuelve el tamaño del búfer de bytes necesario para contener el `TOKEN_PRIVILEGES` estructura representada por el `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Recupera los identificadores locales únicos (LUID) y marcas de atributo de la `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Recupera los nombres de privilegios y marcas de atributo de la `CTokenPrivileges` objeto.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Devuelve un puntero a la `TOKEN_PRIVILEGES` estructura.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Recupera el atributo asociado con el nombre de un privilegio determinado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Convierte un valor a un puntero a la `TOKEN_PRIVILEGES` estructura.|
|[CTokenPrivileges::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/desktop/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema de Windows.

El token de acceso se utiliza para describir los diversos privilegios de seguridad concedidos a cada usuario. Un privilegio consta de un número de 64 bits que se llama a un identificador local único ( [LUID](/windows/desktop/api/winnt/ns-winnt-_luid)) y una cadena de descriptor.

El `CTokenPrivileges` clase es un contenedor para el [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) estructurar y contiene 0 o más privilegios. Pueden agregarse privilegios eliminado, o puede consultarse mediante los métodos de clase proporcionada.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="add"></a>  CTokenPrivileges::Add

Agrega uno o más privilegios para la `CTokenPrivileges` objeto de token de acceso.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H.

*bEnable*<br/>
Si es true, se habilita el privilegio. Si es false, se deshabilita el privilegio.

*rPrivileges*<br/>
Hacer referencia a un [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) estructura. Los privilegios y los atributos se copió esta estructura y se agregan a la `CTokenPrivileges` objeto.

### <a name="return-value"></a>Valor devuelto

La primera forma de este método devuelve true si los privilegios se han agregado correctamente, false en caso contrario.

##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges

El constructor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `CTokenPrivileges` objeto que se va a asignar al nuevo objeto.

*rPrivileges*<br/>
El [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) para asignar a la nueva estructura de `CTokenPrivileges` objeto.

### <a name="remarks"></a>Comentarios

El `CTokenPrivileges` , opcionalmente, se puede crear el objeto utilizando un `TOKEN_PRIVILEGES` definida previamente o estructura `CTokenPrivileges` objeto.

##  <a name="dtor"></a>  CTokenPrivileges::~CTokenPrivileges

Destructor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados.

##  <a name="delete"></a>  CTokenPrivileges::Delete

Elimina un privilegio de la `CTokenPrivileges` objeto de token de acceso.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H. Por ejemplo, podría especificar este parámetro la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege".

### <a name="return-value"></a>Valor devuelto

Devuelve true si se ha eliminado correctamente el privilegio.

### <a name="remarks"></a>Comentarios

Este método resulta útil como herramienta para la creación de símbolos (token) restringido.

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

Elimina todos los privilegios de la `CTokenPrivileges` objeto de token de acceso.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Comentarios

Elimina todos los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso.

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

Recupera nombres para mostrar los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDisplayNames*<br/>
Puntero a una matriz de objetos `CString`. `CNames` se define como una definición de tipo: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Comentarios

El parámetro `pDisplayNames` es un puntero a una matriz de `CString` objetos que recibirán los nombres para mostrar correspondiente a los privilegios incluidos en el `CTokenPrivileges` objeto. Este método recupera nombres para mostrar solo los privilegios especificados en la sección privilegios definidos de WINNT. H.

Este método recupera un nombre que se puede mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre que se puede mostrar es "Forzar el apagado de un sistema remoto". Para obtener el nombre del sistema, use [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

Devuelve el número de entradas de privilegios en el `CTokenPrivileges` objeto.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de privilegios incluidos en el `CTokenPrivileges` objeto.

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

Devuelve la longitud de la `CTokenPrivileges` objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes necesario para contener un `TOKEN_PRIVILEGES` estructura representada por el `CTokenPrivileges` objeto, incluidas todas las entradas de privilegio que contiene.

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

Recupera los identificadores locales únicos (LUID) y marcas de atributo de la `CTokenPrivileges` objeto.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*<br/>
Puntero a una matriz de [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) objetos. `CLUIDArray` se define una definición de tipo como `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Puntero a una matriz de objetos DWORD. Si este parámetro se omite o NULL, no se recuperan los atributos. `CAttributes` se define una definición de tipo como `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los privilegios incluidos en el `CTokenPrivileges` objeto de token de acceso y coloque el LUID individuales y (opcionalmente) los marcadores de atributo en los objetos de matriz.

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

Recupera las marcas de nombre y el atributo desde el `CTokenPrivileges` objeto.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pNames*<br/>
Puntero a una matriz de `CString` objetos. `CNames` se define una definición de tipo como `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Puntero a una matriz de objetos DWORD. Si este parámetro se omite o NULL, no se recuperan los atributos. `CAttributes` se define una definición de tipo como `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los privilegios incluidos en el `CTokenPrivileges` objeto, colocar el nombre y (opcionalmente) en las marcas de atributo en los objetos de matriz.

Este método recupera el nombre del atributo, en lugar de con el nombre que se puede mostrar: por ejemplo, si el nombre del atributo es SE_REMOTE_SHUTDOWN_NAME, el nombre del sistema es "SeRemoteShutdownPrivilege." Para obtener el nombre que se pueden mostrar, use el método [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

Devuelve un puntero a la `TOKEN_PRIVILEGES` estructura.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) estructura.

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

Recupera el atributo asociado con el nombre de un privilegio determinado.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena terminada en null que especifica el nombre del privilegio, tal como se define en el archivo WINNT. Archivo de encabezado H. Por ejemplo, podría especificar este parámetro la constante SE_SECURITY_NAME, o su cadena correspondiente, "SeSecurityPrivilege".

*pdwAttributes*<br/>
Puntero a una variable que recibe los atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el atributo es se ha recuperado correctamente.

##  <a name="operator_eq"></a>  CTokenPrivileges::operator =

Operador de asignación.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
El [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) estructura para asignar a la `CTokenPrivileges` objeto.

*rhs*<br/>
La `CTokenPrivileges` objeto que se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el texto actualizado `CTokenPrivileges` objeto.

##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator const TOKEN_PRIVILEGES \*

Convierte un valor a un puntero a la `TOKEN_PRIVILEGES` estructura.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Convierte un valor a un puntero a la [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) estructura.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
