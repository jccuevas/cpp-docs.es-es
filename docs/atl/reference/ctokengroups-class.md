---
title: Clase CTokenGroups
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 1e9d21c59eb5efabf036fbc938a40de2c4b7a0b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330551"
---
# <a name="ctokengroups-class"></a>Clase CTokenGroups

Esta clase es un `TOKEN_GROUPS` contenedor para la estructura.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CTokenGroups
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|El constructor.|
|[CTokenGroups::-CTokenGroups](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenGroups::Add](#add)|Agrega una `CSid` estructura `TOKEN_GROUPS` o `CTokenGroups` una estructura existente al objeto.|
|[CTokenGroups::Delete](#delete)|Elimina a `CSid` y sus atributos asociados del `CTokenGroups` objeto.|
|[CTokenGroups::DeleteAll](#deleteall)|Elimina todos `CSid` los objetos y `CTokenGroups` sus atributos asociados del objeto.|
|[CTokenGroups::GetCount](#getcount)|Devuelve el `CSid` número de objetos y `CTokenGroups` atributos asociados contenidos en el objeto.|
|[CTokenGroups::GetLength](#getlength)|Devuelve el tamaño `CTokenGroups` del objeto.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Recupera un puntero `TOKEN_GROUPS` a la estructura.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Recupera los `CSid` objetos y `CTokenGroups` atributos que pertenecen al objeto.|
|[CTokenGroups::LookupSid](#lookupsid)|Recupera los atributos `CSid` asociados a un objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Convierte el `CTokenGroups` objeto en un `TOKEN_GROUPS` puntero a la estructura.|
|[CTokenGroups::operator ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

Un token de [acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

La `CTokenGroups` clase es un contenedor para la estructura [de TOKEN_GROUPS,](/windows/win32/api/winnt/ns-winnt-token_groups) que contiene información sobre los identificadores de seguridad de grupo (SD) en un token de acceso.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Add

Agrega una `CSid` estructura `TOKEN_GROUPS` o `CTokenGroups` una estructura existente al objeto.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Un [CSid](../../atl/reference/csid-class.md) objeto.

*dwAttributes*<br/>
Los atributos que `CSid` se van a asociar con el objeto.

*rTokenGroups*<br/>
Una estructura [TOKEN_GROUPS.](/windows/win32/api/winnt/ns-winnt-token_groups)

### <a name="remarks"></a>Observaciones

Estos métodos agregan `CSid` uno o más `CTokenGroups` objetos y sus atributos asociados al objeto.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups

El constructor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CTokenGroups` o [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) estructura con `CTokenGroups` la que se va a construir el objeto.

### <a name="remarks"></a>Observaciones

El `CTokenGroups` objeto se puede crear `TOKEN_GROUPS` opcionalmente utilizando una estructura o un objeto definido `CTokenGroups` previamente.

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups::-CTokenGroups

Destructor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos asignados.

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete

Elimina a `CSid` y sus atributos asociados del `CTokenGroups` objeto.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
El [cSid](../../atl/reference/csid-class.md) objeto para el que se deben quitar el identificador de seguridad (SID) y los atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true `CSid` si se quita, false en caso contrario.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll

Elimina todos `CSid` los objetos y `CTokenGroups` sus atributos asociados del objeto.

```
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount

Devuelve el `CSid` número de `CTokenGroups`objetos contenidos en .

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de [CSid](../../atl/reference/csid-class.md) objetos y `CTokenGroups` sus atributos asociados contenidos en el objeto.

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength

Devuelve el tamaño `CTokenGroup` del objeto.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve el tamaño `CTokenGroup` total del objeto, en bytes.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Recupera un puntero `TOKEN_GROUPS` a la estructura.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Recupera un puntero a la estructura `CTokenGroups` [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) que pertenece al objeto de token de acceso.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Recupera los `CSid` objetos y (opcionalmente) `CTokenGroups` los atributos que pertenecen al objeto.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*<br/>
Puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.

*pAtributos*<br/>
Puntero a una matriz de DORD. Si se omite este parámetro o NULL, no se recuperan los atributos.

### <a name="remarks"></a>Observaciones

Este método enumerará todos `CSid` los objetos `CTokenGroups` contenidos en el objeto y los colocará y (opcionalmente) las marcas de atributo en objetos de matriz.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::LookupSid

Recupera los atributos `CSid` asociados a un objeto.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
El [cSid](../../atl/reference/csid-class.md) objeto.

*pdwAttributes*<br/>
Puntero a un DWORD `CSid` que aceptará el atributo del objeto. Si se omite o NULL, no se recuperará el atributo.

### <a name="return-value"></a>Valor devuelto

Devuelve true `CSid` si se encuentra, false en caso contrario.

### <a name="remarks"></a>Observaciones

Establecer *pdwAttributes* en NULL proporciona una manera `CSid` de confirmar la existencia de la sin tener acceso al atributo. Tenga en cuenta que este método no se debe utilizar para comprobar los derechos de acceso. En su lugar, las aplicaciones deben usar el [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) método.

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::operator ?

Operador de asignación.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CTokenGroups` o [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) estructura que `CTokenGroups` se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CTokenGroups` objeto actualizado.

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *

Convierte un valor en un `TOKEN_GROUPS` puntero a la estructura.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Observaciones

Convierte un valor en un puntero a la [estructura TOKEN_GROUPS.](/windows/win32/api/winnt/ns-winnt-token_groups)

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[Clase CSid](../../atl/reference/csid-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
