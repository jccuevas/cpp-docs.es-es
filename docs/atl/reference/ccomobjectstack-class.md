---
title: Clase CComObjectStack | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComObjectStack
- ATL.CComObjectStack
- ATL::CComObjectStack<Base>
- ATL.CComObjectStack<Base>
- CComObjectStack
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: 19
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 0738eae13fdca5906596194016ce22812fbfcd36
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectstack-class"></a>Clase CComObjectStack
Esta clase crea un objeto COM temporal y le proporciona una implementación básica de **IUnknown**.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class  Base>  
class CComObjectStack
 : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de cualquier otra interfaz que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|El constructor.|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|Devuelve cero. En modo de depuración, se llama `_ASSERTE`.|  
|[CComObjectStack::QueryInterface](#queryinterface)|Devuelve **E_NOINTERFACE**. En modo de depuración, se llama `_ASSERTE`.|  
|[CComObjectStack::Release](#release)|Devuelve cero. En modo de depuración, se llama `_ASSERTE`. ~|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el **HRESULT** devuelto durante la construcción de la `CComObjectStack` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectStack`se utiliza para crear un objeto COM temporal y proporcionar el objeto en una implementación básica de **IUnknown**. Normalmente, el objeto se utiliza como una variable local dentro de una función (que es, se inserta en la pila). Puesto que el objeto se destruye cuando finaliza la función, el recuento de referencias no se realiza para aumentar la eficacia.  
  
 En el ejemplo siguiente se muestra cómo crear un objeto COM utilizado dentro de una función:  
  
 [!code-cpp[NVC_ATL_COM&#42;](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 El objeto temporal `Tempobj` se inserta en la pila y desaparecerán automáticamente cuando finaliza la función.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::AddRef  
 Devuelve cero.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, se llama `_ASSERTE`.  
  
##  <a name="a-nameccomobjectstacka--ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack  
 El constructor.  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas `FinalConstruct` y, a continuación, se establece [m_hResFinalConstruct](#m_hresfinalconstruct) a la `HRESULT` devuelto por `FinalConstruct`. Si no se ha derivado la clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propio `FinalConstruct` método. El destructor llama a `FinalRelease`.  
  
##  <a name="a-namedtora--ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack:: ~ CComObjectStack  
 Destructor.  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="a-namemhresfinalconstructa--ccomobjectstackmhresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct  
 Contiene el `HRESULT` devuelve la llamada `FinalConstruct` durante la construcción de la `CComObjectStack` objeto.  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="a-namequeryinterfacea--ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface  
 Devuelve **E_NOINTERFACE**.  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOINTERFACE**.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, se llama `_ASSERTE`.  
  
##  <a name="a-namereleasea--ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Release  
 Devuelve cero.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, se llama `_ASSERTE`.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Clase CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

