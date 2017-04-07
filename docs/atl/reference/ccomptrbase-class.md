---
title: Clase CComPtrBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
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
ms.openlocfilehash: 28207e483b0bf56b9e3e98f487d174b8ae47e9e7
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptrbase-class"></a>Clase CComPtrBase
Esta clase proporciona una base para usar las rutinas de memoria basado en COM de clases de punteros inteligentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de objeto que hace referencia el puntero inteligente.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[¡CComPtrBase:: Advise](#advise)|Llamar a este método para crear una conexión entre el `CComPtrBase`del punto de conexión y el receptor de un cliente.|  
|[CComPtrBase::Attach](#attach)|Llamar a este método para tomar posesión de un puntero existente.|  
|[CComPtrBase:: CoCreateInstance](#cocreateinstance)|Llamar a este método para crear un objeto de la clase asociada con un Id. de clase especificado o el Id. de programa|  
|[CComPtrBase::CopyTo](#copyto)|Llamar a este método para copiar el `CComPtrBase` puntero a otra variable de puntero.|  
|[CComPtrBase::Detach](#detach)|Llamar a este método para liberar la propiedad de un puntero.|  
|[CComPtrBase::IsEqualObject](#isequalobject)|Llamar a este método para comprobar si especificado **IUnknown** señala al mismo objeto asociado a la `CComPtrBase` objeto.|  
|[CComPtrBase::QueryInterface](#queryinterface)|Llame a este método para devolver un puntero a una interfaz especificada.|  
|[CComPtrBase::Release](#release)|Llame a este método para liberar la interfaz.|  
|[CComPtrBase::SetSite](#setsite)|Llamar a este método para establecer el sitio de la `CComPtrBase` objeto a la **IUnknown** del objeto primario.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|El operador de conversión.|  
|[¡CComPtrBase::operator!](#operator_not)|El operador NOT.|  
|[CComPtrBase::operator aspecto](#operator_amp)|El aspecto de operador.|  
|[CComPtrBase::operator *](#operator_star)|El * (operador).|  
|[CComPtrBase::operator](#ccomptrbase__operator lt)|El menor-que el operador.|  
|[CComPtrBase::operator ==](#operator_eq_eq)|El operador de igualdad.|  
|[CComPtrBase::operator->](#operator_ptr)|El operador de miembros de puntero.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|La variable de miembro de datos de puntero.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona la base para otros punteros inteligentes que utilizan rutinas de administración de memoria COM, como [CComQIPtr](../../atl/reference/ccomqiptr-class.md) y [CComPtr](../../atl/reference/ccomptr-class.md). Agregar sus propios operadores y constructores de las clases derivadas, pero se basan en los métodos proporcionados por `CComPtrBase`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  
  
##  <a name="advise"></a>¡CComPtrBase:: Advise  
 Llamar a este método para crear una conexión entre el `CComPtrBase`del punto de conexión y el receptor de un cliente.  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 Un puntero al cliente **IUnknown**.  
  
 `iid`  
 El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.  
  
 `pdw`  
 Puntero a la cookie que identifica de forma única la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [AtlAdvise](http://msdn.microsoft.com/library/625a2f03-6b7f-4761-be5d-d2871d1d3254) para obtener más información.  
  
##  <a name="attach"></a>CComPtrBase::Attach  
 Llamar a este método para tomar posesión de un puntero existente.  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p2`  
 La `CComPtrBase` objeto tomará posesión de este puntero.  
  
### <a name="remarks"></a>Comentarios  
 **Adjuntar** llamadas [CComPtrBase::Release](#release) en existente [CComPtrBase::p](#p) variable miembro y, a continuación, asigna `p2` a `CComPtrBase::p`. Cuando un `CComPtrBase` objeto toma posesión de un puntero, llama automáticamente a `Release` en el puntero que se eliminará el puntero y los datos asignados si el recuento de referencias en el objeto que se va a 0.  
  
##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 Destructor.  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera la interfaz señalada por `CComPtrBase`.  
  
##  <a name="cocreateinstance"></a>CComPtrBase:: CoCreateInstance  
 Llamar a este método para crear un objeto de la clase asociada con un Id. de clase especificado o el Id. de programa  
  
```
HRESULT CoCreateInstance(  
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(  
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szProgID`  
 Puntero a un ProgID, que se utiliza para recuperar el CLSID.  
  
 `pUnkOuter`  
 Si **NULL**, indica que el objeto no se está creando como parte de un agregado. Si no es **NULL**, es un puntero al objeto agregado **IUnknown** interfaz (el control **IUnknown**).  
  
 `dwClsContext`  
 Contexto en el que se ejecutará el código que administra el objeto recién creado.  
  
 `rclsid`  
 CLSID asociado con los datos y el código que se utilizará para crear el objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 En caso de error, devuelve S_OK éxito, o REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING o E_NOINTERFACE. Consulte [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) y [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) para obtener una descripción de estos errores.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a la primera forma del método, [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) se usa para recuperar el CLSID. Ambas formas, a continuación, llame a [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
 En compilaciones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.  
  
##  <a name="copyto"></a>CComPtrBase::CopyTo  
 Llamar a este método para copiar el `CComPtrBase` puntero a otra variable de puntero.  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *ppT*  
 Dirección de la variable que recibirá el `CComPtrBase` puntero.  
  
### <a name="return-value"></a>Valor devuelto  
 En caso de éxito, E_POINTER en caso de error, devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Copia la `CComPtrBase` puntero a *ppT*. El recuento de referencias el [CComPtrBase::p](#p) se incrementa una variable miembro.  
  
 Un error HRESULT que se devolverá si *ppT* es igual a NULL. En compilaciones de depuración, se producirá un error de aserción si *ppT* es igual a NULL.  
  
##  <a name="detach"></a>CComPtrBase::Detach  
 Llamar a este método para liberar la propiedad de un puntero.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia del puntero.  
  
### <a name="remarks"></a>Comentarios  
 Libera la posesión de un puntero, se establece la [CComPtrBase::p](#p) variable de miembro de datos en NULL y devuelve una copia del puntero.  
  
##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 Llamar a este método para comprobar si especificado **IUnknown** señala al mismo objeto asociado a la `CComPtrBase` objeto.  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pOther`  
 El **IUnknown \* ** para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los objetos son idénticos.  
  
##  <a name="operator_not"></a>¡CComPtrBase::operator!  
 El operador NOT.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el `CComHeapPtr` puntero es igual a NULL, false en caso contrario.  
  
##  <a name="operator_amp"></a>CComPtrBase::operator&amp;  
 El aspecto de operador.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la dirección del objeto indicado por la `CComPtrBase` objeto.  
  
##  <a name="operator_star"></a>CComPtrBase::operator *  
 El * (operador).  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de [CComPtrBase::p](#p); es decir, un puntero al objeto al que hace referencia la `CComPtrBase` objeto.  
  
 Si las versiones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.  
  
##  <a name="operator_eq_eq"></a>CComPtrBase::operator ==  
 El operador de igualdad.  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pT*  
 Un puntero a un objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si `CComPtrBase` y *pT* indican el mismo objeto, false en caso contrario.  
  
##  <a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 El operador de puntero a miembro.  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la [CComPtrBase::p](#p) variable de miembro de datos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este operador para llamar a un método en una clase que apunta la `CComPtrBase` objeto. En compilaciones de depuración, se producirá un error de aserción si el `CComPtrBase` miembro de datos señala a NULL.  
  
##  <a name="operator_lt"></a>CComPtrBase::operator&lt;  
 El menor-que el operador.  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pT*  
 Un puntero a un objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el puntero administrado por el objeto actual es menor que el puntero a la que se está comparando.  
  
##  <a name="operator_t_star"></a>CComPtrBase::operator T *  
 El operador de conversión.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.  
  
##  <a name="p"></a>CComPtrBase::p  
 La variable de miembro de datos de puntero.  
  
```
T* p;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable miembro contiene la información de puntero.  
  
##  <a name="queryinterface"></a>CComPtrBase::QueryInterface  
 Llame a este método para devolver un puntero a una interfaz especificada.  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `Q`  
 El tipo de objeto cuyo puntero de interfaz es necesario.  
  
 `pp`  
 Dirección de la variable de salida que recibe el puntero de interfaz solicitada.  
  
### <a name="return-value"></a>Valor devuelto  
 En caso de error, devuelve S_OK éxito o E_NOINTERFACE.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [IUnknown:: QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 En compilaciones de depuración, se producirá un error de aserción si *pp* no es igual a NULL.  
  
##  <a name="release"></a>CComPtrBase::Release  
 Llame a este método para liberar la interfaz.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 La interfaz se libera, y [CComPtrBase::p](#p) se establece en NULL.  
  
##  <a name="setsite"></a>CComPtrBase::SetSite  
 Llamar a este método para establecer el sitio de la `CComPtrBase` objeto a la **IUnknown** del objeto primario.  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `punkParent`  
 Un puntero a la **IUnknown** interfaz del elemento primario.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [AtlSetChildSite](http://msdn.microsoft.com/library/2a8ece19-6bfd-4e89-9d1d-e5a78f95e2df).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

