---
title: Clase CComObjectGlobal | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d5264a2ab8e1bbc4c3f4eac4d83d096d91e8846
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectglobal-class"></a>Clase CComObjectGlobal
Esta clase administra un recuento de referencias en el módulo que contiene el `Base` objeto.  
  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|El constructor.|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|Implementa un global `AddRef`.|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementa un global `QueryInterface`.|  
|[CComObjectGlobal::Release](#release)|Implementa un global **versión**.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el **HRESULT** devuelto durante la construcción de la `CComObjectGlobal` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectGlobal`administra un recuento de referencias en el módulo que contiene el `Base` objeto. `CComObjectGlobal`garantiza que no se eliminará el objeto siempre y cuando el módulo no está disponible. Cuando el recuento de referencias en todo el módulo llega a cero, solo se quitará el objeto.  
  
 Por ejemplo, si se usa `CComObjectGlobal`, un generador de clases puede contener un objeto global común compartido por todos sus clientes.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>CComObjectGlobal::AddRef  
 Incrementa el recuento de referencias del objeto en 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico y prueba.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `AddRef` llamadas **_Module::Lock**, donde **_Module** es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
##  <a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 El constructor. Llamadas `FinalConstruct` y, a continuación, establece [m_hResFinalConstruct](#m_hresfinalconstruct) a la `HRESULT` devuelto por `FinalConstruct`.  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>Comentarios  
 Si no se ha derivado su clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar sus propios `FinalConstruct` método. El destructor llama a `FinalRelease`.  
  
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
 [in] El GUID de la interfaz que se solicita.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por iid, o **NULL** si no se encuentra la interfaz.  
  
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
 En las compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico y prueba. En las compilaciones de depuración no, **versión** siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, **versión** llamadas **_Module::Unlock**, donde **_Module** es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComObjectStack](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
