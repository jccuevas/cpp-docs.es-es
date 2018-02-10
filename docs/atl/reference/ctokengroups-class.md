---
title: Clase CTokenGroups | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a5a958fcc1bd8c26599272774c86cd64fa2c720
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="ctokengroups-class"></a>Clase CTokenGroups
Esta clase es un contenedor para la **TOKEN_GROUPS** estructura.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CTokenGroups
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](#ctokengroups)|El constructor.|  
|[CTokenGroups::~CTokenGroups](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTokenGroups::Add](#add)|Agrega un `CSid` o existente **TOKEN_GROUPS** estructura especificada en el `CTokenGroups` objeto.|  
|[CTokenGroups::Delete](#delete)|Elimina un `CSid` y sus atributos asociados de la `CTokenGroups` objeto.|  
|[CTokenGroups::DeleteAll](#deleteall)|Todos los elimina `CSid` objetos y sus atributos asociados de la `CTokenGroups` objeto.|  
|[CTokenGroups::GetCount](#getcount)|Devuelve el número de `CSid` objetos y atributos asociados, incluidos en el **CTokenGroups** objeto.|  
|[CTokenGroups::GetLength](#getlength)|Devuelve el tamaño de la `CTokenGroups` objeto.|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Recupera un puntero a la **TOKEN_GROUPS** estructura.|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Recupera el `CSid` objetos y atributos que pertenecen a la `CTokenGroups` objeto.|  
|[CTokenGroups::LookupSid](#lookupsid)|Recupera los atributos asociados con un `CSid` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[TOKEN_GROUPS const CTokenGroups::operator *](#operator_const_token_groups__star)|Convierte el `CTokenGroups` objeto a un puntero a la **TOKEN_GROUPS** estructura.|  
|[CTokenGroups::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Un [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que haya iniciado sesión en un sistema de Windows.  
  
 El **CTokenGroups** clase es un contenedor para la [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura, que contiene información acerca de los identificadores de seguridad (SID) de grupo en un token de acceso.  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [el Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="add"></a>CTokenGroups::Add  
 Agrega un `CSid` o existente **TOKEN_GROUPS** estructura especificada en el `CTokenGroups` objeto.  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md) objeto.  
  
 `dwAttributes`  
 Los atributos para asociar la `CSid` objeto.  
  
 *rTokenGroups*  
 A [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Estos métodos agregan uno o varios `CSid` objetos y sus atributos asociados a la `CTokenGroups` objeto.  
  
##  <a name="ctokengroups"></a>CTokenGroups::CTokenGroups  
 El constructor.  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `CTokenGroups` objeto o [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura con la que se va a construir el `CTokenGroups` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CTokenGroups` , opcionalmente, se puede crear el objeto con un **TOKEN_GROUPS** definida previamente o estructura `CTokenGroups` objeto.  
  
##  <a name="dtor"></a>  CTokenGroups::~CTokenGroups  
 Destructor.  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera todos los recursos asignados.  
  
##  <a name="delete"></a>CTokenGroups::Delete  
 Elimina un `CSid` y sus atributos asociados de la `CTokenGroups` objeto.  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 El [CSid](../../atl/reference/csid-class.md) objeto para el que se deben quitar el identificador de seguridad (SID) y atributos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el `CSid` se quita, false en caso contrario.  
  
##  <a name="deleteall"></a>  CTokenGroups::DeleteAll  
 Todos los elimina `CSid` objetos y sus atributos asociados de la `CTokenGroups` objeto.  
  
```
void DeleteAll() throw();
```  
  
##  <a name="getcount"></a>  CTokenGroups::GetCount  
 Devuelve el número de `CSid` objetos incluidos en `CTokenGroups`.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de [CSid](../../atl/reference/csid-class.md) objetos y sus atributos asociados, incluidos en el `CTokenGroups` objeto.  
  
##  <a name="getlength"></a>CTokenGroups::GetLength  
 Devuelve el tamaño de la **CTokenGroup** objeto.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el tamaño total de la **CTokenGroup** objeto, en bytes.  
  
##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS  
 Recupera un puntero a la **TOKEN_GROUPS** estructura.  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera un puntero a la [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura que pertenecen a la `CTokenGroups` objeto de token de acceso.  
  
##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes  
 Recupera el `CSid` objetos y (opcionalmente) los atributos que pertenecen a la `CTokenGroups` objeto.  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSids`  
 Puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.  
  
 `pAttributes`  
 Puntero a una matriz de valores DWORD. Si este parámetro se omite o NULL, no se obtienen los atributos.  
  
### <a name="remarks"></a>Comentarios  
 Este método enumerará todos los `CSid` objetos incluidos en el `CTokenGroups` de objetos y colocar ellos y (opcionalmente) los marcadores de atributo en objetos de matriz.  
  
##  <a name="lookupsid"></a>  CTokenGroups::LookupSid  
 Recupera los atributos asociados con un `CSid` objeto.  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 El [CSid](../../atl/reference/csid-class.md) objeto.  
  
 `pdwAttributes`  
 Puntero a un valor de DWORD que aceptará la `CSid` atributo del objeto. Si se omite o es NULL, no se recuperará el atributo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el `CSid` se encuentra, false en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Establecer `pdwAttributes` a NULL proporciona una manera de confirmar la existencia de la `CSid` sin tener acceso a los atributos. Tenga en cuenta que este método no debe usarse para comprobar los derechos de acceso. Las aplicaciones deberían usar el [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) método.  
  
##  <a name="operator_eq"></a>CTokenGroups::operator =  
 Operador de asignación.  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `CTokenGroups` objeto o [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura para asignar a la `CTokenGroups` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la actualización `CTokenGroups` objeto.  
  
##  <a name="operator_const_token_groups__star"></a>TOKEN_GROUPS const CTokenGroups::operator *  
 Convierte un valor a un puntero a la **TOKEN_GROUPS** estructura.  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>Comentarios  
 Convierte un valor a un puntero a la [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) estructura.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [CSid (clase)](../../atl/reference/csid-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
