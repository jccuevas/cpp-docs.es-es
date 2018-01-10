---
title: Clase CComObjectStack | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs: C++
helpviewer_keywords: CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b7fa9d14a27277d4c26fc6e7589400e19ef1395
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|El constructor.|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|Devuelve el valor cero. En modo de depuración, llama a `_ASSERTE`.|  
|[CComObjectStack::QueryInterface](#queryinterface)|Devuelve **E_NOINTERFACE**. En modo de depuración, llama a `_ASSERTE`.|  
|[CComObjectStack::Release](#release)|Devuelve el valor cero. En modo de depuración, llama a `_ASSERTE`. ~|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el **HRESULT** devuelto durante la construcción de la `CComObjectStack` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectStack`se utiliza para crear un objeto COM temporal y proporcionar el objeto de una implementación básica de **IUnknown**. Normalmente, el objeto se usa como una variable local dentro de una función (que es, se inserta en la pila). Puesto que el objeto se destruye cuando se termina la función, el recuento de referencias no se realiza para aumentar la eficacia.  
  
 En el ejemplo siguiente se muestra cómo crear un objeto COM que se usa dentro de una función:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 El objeto temporal `Tempobj` se inserta en la pila y desaparece automáticamente cuando finaliza la función.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>CComObjectStack::AddRef  
 Devuelve el valor cero.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor cero.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, llama a `_ASSERTE`.  
  
##  <a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack  
 El constructor.  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas `FinalConstruct` y, a continuación, establece [m_hResFinalConstruct](#m_hresfinalconstruct) a la `HRESULT` devuelto por `FinalConstruct`. Si no se ha derivado su clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar sus propios `FinalConstruct` método. El destructor llama a `FinalRelease`.  
  
##  <a name="dtor"></a>CComObjectStack:: ~ CComObjectStack  
 Destructor.  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct  
 Contiene el `HRESULT` procedentes de la llamada `FinalConstruct` durante la construcción de la `CComObjectStack` objeto.  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectStack::QueryInterface  
 Devuelve **E_NOINTERFACE**.  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOINTERFACE**.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, llama a `_ASSERTE`.  
  
##  <a name="release"></a>CComObjectStack::Release  
 Devuelve el valor cero.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor cero.  
  
### <a name="remarks"></a>Comentarios  
 En modo de depuración, llama a `_ASSERTE`.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Clase CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
