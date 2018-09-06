---
title: CTokenGroups (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87109793625435945c45b2643ccd674946acff49
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752650"
---
# <a name="ctokengroups-class"></a>CTokenGroups (clase)

Esta clase es un contenedor para el `TOKEN_GROUPS` estructura.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CTokenGroups
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|El constructor.|
|[CTokenGroups:: ~ CTokenGroups](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenGroups::Add](#add)|Agrega un `CSid` o existentes `TOKEN_GROUPS` estructura a la `CTokenGroups` objeto.|
|[CTokenGroups::Delete](#delete)|Elimina un `CSid` y sus atributos asociados desde el `CTokenGroups` objeto.|
|[CTokenGroups::DeleteAll](#deleteall)|Todos los elimina `CSid` objetos y sus atributos asociados desde el `CTokenGroups` objeto.|
|[CTokenGroups::GetCount](#getcount)|Devuelve el número de `CSid` objetos y atributos asociados, incluidos en el `CTokenGroups` objeto.|
|[CTokenGroups::GetLength](#getlength)|Devuelve el tamaño de la `CTokenGroups` objeto.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Recupera un puntero a la `TOKEN_GROUPS` estructura.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Recupera el `CSid` objetos y atributos que pertenecen a la `CTokenGroups` objeto.|
|[CTokenGroups::LookupSid](#lookupsid)|Recupera los atributos asociados con un `CSid` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Convierte el `CTokenGroups` objeto a un puntero a la `TOKEN_GROUPS` estructura.|
|[CTokenGroups::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/desktop/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema de Windows.

El `CTokenGroups` clase es un contenedor para el [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura, que contiene información acerca de los identificadores de seguridad (SID) de grupo en un token de acceso.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="add"></a>  CTokenGroups::Add

Agrega un `CSid` o existentes `TOKEN_GROUPS` estructura a la `CTokenGroups` objeto.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*  
Un [CSid](../../atl/reference/csid-class.md) objeto.

*dwAttributes*  
Los atributos que se va a asociar con el `CSid` objeto.

*rTokenGroups*  
Un [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura.

### <a name="remarks"></a>Comentarios

Estos métodos agregan uno o varios `CSid` objetos y sus atributos asociados a la `CTokenGroups` objeto.

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

El constructor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*RHS*  
El `CTokenGroups` objeto o [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura con la que se va a construir el `CTokenGroups` objeto.

### <a name="remarks"></a>Comentarios

El `CTokenGroups` , opcionalmente, se puede crear el objeto utilizando un `TOKEN_GROUPS` definida previamente o estructura `CTokenGroups` objeto.

##  <a name="dtor"></a>  CTokenGroups:: ~ CTokenGroups

Destructor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos asignados.

##  <a name="delete"></a>  CTokenGroups::Delete

Elimina un `CSid` y sus atributos asociados desde el `CTokenGroups` objeto.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parámetros

*rSid*  
El [CSid](../../atl/reference/csid-class.md) objeto para el que se deben quitar el identificador de seguridad (SID) y atributos.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el `CSid` se quita, false en caso contrario.

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

Todos los elimina `CSid` objetos y sus atributos asociados desde el `CTokenGroups` objeto.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

Devuelve el número de `CSid` los objetos contenidos en `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de [CSid](../../atl/reference/csid-class.md) objetos y sus atributos asociados, incluidos en el `CTokenGroups` objeto.

##  <a name="getlength"></a>  CTokenGroups::GetLength

Devuelve el tamaño de la `CTokenGroup` objeto.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve el tamaño total de la `CTokenGroup` objeto, en bytes.

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

Recupera un puntero a la `TOKEN_GROUPS` estructura.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Recupera un puntero a la [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura que pertenecen a la `CTokenGroups` objeto de token de acceso.

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

Recupera el `CSid` objetos y (opcionalmente) en los atributos que pertenecen a la `CTokenGroups` objeto.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*  
Puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.

*pAttributes*  
Puntero a una matriz de valores DWORD. Si este parámetro se omite o NULL, no se recuperan los atributos.

### <a name="remarks"></a>Comentarios

Este método enumerará todos los `CSid` objetos incluidos en el `CTokenGroups` de objetos y colocar ellos y (opcionalmente) los marcadores de atributo en los objetos de matriz.

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

Recupera los atributos asociados con un `CSid` objeto.

```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*rSid*  
El [CSid](../../atl/reference/csid-class.md) objeto.

*pdwAttributes*  
Puntero a un valor DWORD que aceptará el `CSid` atributo del objeto. Si se omite o es NULL, el atributo no se recuperarán.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el `CSid` se encuentra, false en caso contrario.

### <a name="remarks"></a>Comentarios

Establecer *pdwAttributes* a NULL proporciona una manera de confirmar la existencia de la `CSid` sin tener acceso a los atributos. Tenga en cuenta que este método no debe usarse para comprobar los derechos de acceso. Las aplicaciones deben usar en su lugar el [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) método.

##  <a name="operator_eq"></a>  CTokenGroups::operator =

Operador de asignación.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*RHS*  
El `CTokenGroups` objeto o [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura para asignar a la `CTokenGroups` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el texto actualizado `CTokenGroups` objeto.

##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator const TOKEN_GROUPS *

Convierte un valor a un puntero a la `TOKEN_GROUPS` estructura.

```  
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Convierte un valor a un puntero a la [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) estructura.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../visual-cpp-samples.md)   
[CSid (clase)](../../atl/reference/csid-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)   
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
