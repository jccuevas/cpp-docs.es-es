---
title: Clase CComObjectGlobal | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 8c371eee9de660a2bb08e67f35a5a6c81d32eee0
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectglobal-class"></a>Clase CComObjectGlobal
Esta clase administra un recuento de referencias en el módulo que contiene la `Base` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de cualquier otra interfaz que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|El constructor.|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|Implementa un global `AddRef`.|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementa un global `QueryInterface`.|  
|[CComObjectGlobal::Release](#release)|Implementa un global **versión**.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el **HRESULT** devuelto durante la construcción de la `CComObjectGlobal` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectGlobal`administra un recuento de referencias en el módulo que contiene la `Base` objeto. `CComObjectGlobal`garantiza que no se eliminará el objeto como el módulo no se libera. Cuando el recuento de referencias en todo el módulo llega a cero, sólo se quitará el objeto.  
  
 Por ejemplo, mediante `CComObjectGlobal`, un generador de clases puede contener un objeto global común compartida por todos sus clientes.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>CComObjectGlobal::AddRef  
 El recuento de referencias del objeto se incrementa en 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para los diagnósticos y pruebas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `AddRef` llamadas **_Module::Lock**, donde **_Module** es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
##  <a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 El constructor. Llamadas `FinalConstruct` y, a continuación, se establece [m_hResFinalConstruct](#m_hresfinalconstruct) a la `HRESULT` devuelto por `FinalConstruct`.  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>Comentarios  
 Si no se ha derivado la clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propio `FinalConstruct` método. El destructor llama a `FinalRelease`.  
  
##  <a name="dtor"></a>CComObjectGlobal:: ~ CComObjectGlobal  
 Destructor.  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct  
 Contiene el `HRESULT` de llamar al método `FinalConstruct` durante la construcción de la `CComObjectGlobal` objeto.  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectGlobal::QueryInterface  
 Recupera un puntero al puntero de interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por el iid, o **NULL** si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 `QueryInterface` solo administra interfaces de la tabla de asignación COM.  
  
##  <a name="release"></a>CComObjectGlobal::Release  
 Disminuye el recuento de referencias del objeto en 1.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, **versión** devuelve un valor que puede ser útil para los diagnósticos y pruebas. En versiones no depuradas, **versión** siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, **versión** llamadas **_Module::Unlock**, donde **_Module** es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComObjectStack](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

