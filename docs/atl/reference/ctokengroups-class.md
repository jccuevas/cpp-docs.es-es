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
ms.openlocfilehash: 88096747f45d4a81c873837cdd4975da9d8c24e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496292"
---
# <a name="ctokengroups-class"></a>Clase CTokenGroups

Esta clase es un contenedor para la `TOKEN_GROUPS` estructura.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CTokenGroups
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|El constructor.|
|[CTokenGroups::~CTokenGroups](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenGroups::Add](#add)|Agrega una `CSid` estructura existente `TOKEN_GROUPS` o al `CTokenGroups` objeto.|
|[CTokenGroups::Delete](#delete)|Elimina una `CSid` clase y sus atributos asociados `CTokenGroups` del objeto.|
|[CTokenGroups::DeleteAll](#deleteall)|Elimina todos los `CSid` objetos y sus atributos asociados `CTokenGroups` del objeto.|
|[CTokenGroups::GetCount](#getcount)|Devuelve el número de `CSid` objetos y los atributos asociados contenidos en `CTokenGroups` el objeto.|
|[CTokenGroups::GetLength](#getlength)|Devuelve el tamaño del `CTokenGroups` objeto.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Recupera un puntero a la `TOKEN_GROUPS` estructura.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Recupera los `CSid` objetos y atributos `CTokenGroups` que pertenecen al objeto.|
|[CTokenGroups::LookupSid](#lookupsid)|Recupera los atributos asociados a un `CSid` objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CTokenGroups:: Operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Convierte el `CTokenGroups` objeto en un puntero a la `TOKEN_GROUPS` estructura.|
|[CTokenGroups::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

La `CTokenGroups` clase es un contenedor para la estructura [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) , que contiene información sobre los identificadores de seguridad (SID) de grupo en un token de acceso.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="add"></a>  CTokenGroups::Add

Agrega una `CSid` estructura existente `TOKEN_GROUPS` o al `CTokenGroups` objeto.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto [CSid](../../atl/reference/csid-class.md) .

*dwAttributes*<br/>
Atributos que se van a asociar `CSid` al objeto.

*rTokenGroups*<br/>
Estructura [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) .

### <a name="remarks"></a>Comentarios

Estos métodos agregan uno o `CSid` más objetos y sus atributos asociados `CTokenGroups` al objeto.

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

El constructor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `CTokenGroups` estructura de objeto o [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) con la que se `CTokenGroups` va a construir el objeto.

### <a name="remarks"></a>Comentarios

El `CTokenGroups` objeto se puede crear opcionalmente mediante una `TOKEN_GROUPS` estructura o un objeto definido `CTokenGroups` previamente.

##  <a name="dtor"></a>  CTokenGroups::~CTokenGroups

Destructor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados.

##  <a name="delete"></a>  CTokenGroups::Delete

Elimina una `CSid` clase y sus atributos asociados `CTokenGroups` del objeto.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto [CSid](../../atl/reference/csid-class.md) para el que se deben quitar el identificador de seguridad (SID) y los atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true si se `CSid` quita el, false en caso contrario.

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

Elimina todos los `CSid` objetos y sus atributos asociados `CTokenGroups` del objeto.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

Devuelve el número de `CSid` objetos incluidos en `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de objetos [CSid](../../atl/reference/csid-class.md) y sus atributos asociados contenidos en el `CTokenGroups` objeto.

##  <a name="getlength"></a>  CTokenGroups::GetLength

Devuelve el tamaño del `CTokenGroup` objeto.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve el tamaño total del `CTokenGroup` objeto, en bytes.

##  <a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Recupera un puntero a la `TOKEN_GROUPS` estructura.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Recupera un puntero a la estructura [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) que pertenece al `CTokenGroups` objeto de token de acceso.

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

Recupera los `CSid` objetos y (opcionalmente) los atributos `CTokenGroups` que pertenecen al objeto.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*<br/>
Puntero a una matriz de objetos [CSid](../../atl/reference/csid-class.md) .

*pAttributes*<br/>
Puntero a una matriz de DWORDs. Si este parámetro se omite o es NULL, no se recuperan los atributos.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los `CSid` objetos contenidos en el `CTokenGroups` objeto y los colocará y, opcionalmente, las marcas de atributo en los objetos de matriz.

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

Recupera los atributos asociados a un `CSid` objeto.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto [CSid](../../atl/reference/csid-class.md) .

*pdwAttributes*<br/>
Puntero a un valor DWORD que aceptará `CSid` el atributo del objeto. Si se omite o es NULL, el atributo no se recuperará.

### <a name="return-value"></a>Valor devuelto

Devuelve true si `CSid` se encuentra, false en caso contrario.

### <a name="remarks"></a>Comentarios

Establecer *pdwAttributes* en NULL proporciona una manera de confirmar la existencia de `CSid` sin tener acceso al atributo. Tenga en cuenta que este método no se debe usar para comprobar los derechos de acceso. En su lugar, las aplicaciones deben usar el método [CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) .

##  <a name="operator_eq"></a>CTokenGroups:: Operator =

Operador de asignación.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `CTokenGroups` estructura de objeto o [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) `CTokenGroups` que se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CTokenGroups` actualizado.

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: Operator const TOKEN_GROUPS *

Convierte un valor en un puntero a la `TOKEN_GROUPS` estructura.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Convierte un valor en un puntero a la estructura [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) .

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[CSid (clase)](../../atl/reference/csid-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
