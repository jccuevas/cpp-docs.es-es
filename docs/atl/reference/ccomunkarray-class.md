---
title: Clase CComUnkArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 94f1062ff3808f527874a8890eca95c9b655b1bf
ms.lasthandoff: 02/24/2017

---
# <a name="ccomunkarray-class"></a>CComUnkArray (clase)
Esta clase almacena **IUnknown** punteros y está diseñado para utilizarse como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>Parámetros  
 *nMaxSize*  
 El número máximo de **IUnknown** punteros que se pueden almacenar en la matriz estática.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|Llamar a este método para agregar una **IUnknown** puntero a la matriz.|  
|[CComUnkArray::begin](#begin)|Devuelve un puntero al primer **IUnknown** puntero en la colección.|  
|[CComUnkArray::end](#end)|Devuelve un puntero a uno más allá de la última **IUnknown** puntero en la colección.|  
|[CComUnkArray::GetCookie](#getcookie)|Llamar a este método para obtener la cookie asociada con un determinado **IUnknown** puntero.|  
|[CComUnkArray::GetUnknown](#getunknown)|Llamar a este método para obtener la **IUnknown** puntero asociado a una cookie determinada.|  
|[CComUnkArray::Remove](#remove)|Llamar a este método para quitar un **IUnknown** puntero de la matriz.|  
  
## <a name="remarks"></a>Comentarios  
 **CComUnkArray** contiene un número fijo de **IUnknown** punteros, cada punto de una interfaz en una conexión. **CComUnkArray** puede utilizarse como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla. **CComUnkArray\<1 >** es una especialización de plantilla de **CComUnkArray** que se ha optimizado para un punto de conexión.  
  
 El **CComUnkArray** métodos [comenzar](#begin) y [final](#end) puede utilizarse para recorrer en iteración todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).  
  
 Consulte [agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md) para obtener más información acerca de cómo automatizar la creación de conexión de punto de proxy.  
  
> [!NOTE]
> **Nota** la clase [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) utiliza la **Agregar clase** asistente al crear un control que tiene puntos de conexión. Si desea especificar manualmente el número de puntos de conexión, cambie la referencia de **CComDynamicUnkArray** a `CComUnkArray<` *n* `>`, donde *n* es el número de puntos de conexión necesarios.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="add"></a>CComUnkArray::Add  
 Llamar a este método para agregar una **IUnknown** puntero a la matriz.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 Llamar a este método para agregar una **IUnknown** puntero a la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cookie asociada con el puntero recién agregado, o 0 si la matriz no es lo suficientemente grande como para contener el nuevo puntero.  
  
##  <a name="begin"></a>CComUnkArray::begin  
 Devuelve un puntero al principio de la colección de **IUnknown** punteros de interfaz.  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un **IUnknown** puntero de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 La colección contiene punteros a las interfaces que se almacena localmente como **IUnknown**. Convierte cada **IUnknown** interfaz para el tipo de interfaz real y, a continuación, llamar a través de él. No es necesario consultar la interfaz primero.  
  
 Antes de utilizar el **IUnknown** interfaz, debe comprobar que no es **NULL**.  
  
##  <a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 El constructor.  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece la colección para contener `nMaxSize` **IUnknown** punteros e inicializa los punteros a **NULL**.  
  
##  <a name="end"></a>CComUnkArray::end  
 Devuelve un puntero a uno más allá de la última **IUnknown** puntero en la colección.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un **IUnknown** puntero de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 El `CComUnkArray` métodos **comenzar** y **final** puede utilizarse para recorrer en bucle todos los puntos de conexión, por ejemplo, cuando se desencadena un evento.  
  
 [!code-cpp[NVC_ATL_COM&#44;](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>CComUnkArray::GetCookie  
 Llamar a este método para obtener la cookie asociada con un determinado **IUnknown** puntero.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppFind`  
 El **IUnknown** puntero para el que se requiere la cookie asociada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cookie asociada con la **IUnknown** puntero, o 0 si no hay coincidencia **IUnknown** se encuentra el puntero.  
  
### <a name="remarks"></a>Comentarios  
 Si hay más de una instancia de la misma **IUnknown** puntero, esta función devuelve la cookie de la primera de ellas.  
  
##  <a name="getunknown"></a>CComUnkArray::GetUnknown  
 Llamar a este método para obtener la **IUnknown** puntero asociado a una cookie determinada.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 Para que la cookie de asociado **IUnknown** puntero es necesario.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el **IUnknown** puntero, o NULL si no se encuentra ninguna cookie de búsqueda de coincidencias.  
  
##  <a name="remove"></a>CComUnkArray::Remove  
 Llamar a este método para quitar un **IUnknown** puntero de la matriz.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 Hacer referencia a la cookie la **IUnknown** puntero va a quitar de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si se quita el puntero, **FALSE** en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [CComDynamicUnkArray (clase)](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

