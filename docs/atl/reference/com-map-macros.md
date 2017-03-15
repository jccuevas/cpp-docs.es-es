---
title: Macros de mapa COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
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
ms.openlocfilehash: 79658b6ac22719af7172c9d2848675faf2a23a0c
ms.lasthandoff: 02/24/2017

---
# <a name="com-map-macros"></a>Macros de mapa COM
Estas macros definen los mapas de interfaz COM.  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|Marca el principio de las entradas del mapa de interfaz COM.|  
|[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)|Introduce las interfaces en el mapa de interfaz COM.|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilice esta macro para eliminar la ambigüedad entre dos ramas de la herencia.|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Use esta macro para entrar en la interfaz en el mapa COM y especificar su IID.|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), salvo que puede especificar un IID diferentes.|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Cuando la interfaz identificado por `iid` se consulta, `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), salvo que consultar los IID da como resultado la consulta de reenvío `punk`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si `punk` es **NULL**, crea automáticamente el agregado descrito por el `clsid`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), salvo que consultar los IID da como resultado la consulta de reenvío `punk`y si `punk` es **NULL**, automáticamente crea el agregado descrito por el `clsid`.|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Hace que el programa llamar a [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) cuando se consulta la interfaz especificada.|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Guarda los datos de la interfaz específica para cada instancia.|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expone las interfaces divisibles.|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Un mecanismo general para enlazar con ATL `QueryInterface` lógica.|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), salvo que consultar los IID da como resultado una llamada a `func`.|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Devuelve **E_NOINTERFACE** y finaliza el procesamiento de mapa COM cuando se consulta la interfaz especificada.|  
|[END_COM_MAP](#end_com_map)|Marca el final de las entradas del mapa de interfaz COM.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="a-namebegincommapa--begincommap"></a><a name="begin_com_map"></a>BEGIN_COM_MAP  
 El mapa COM es el mecanismo que expone interfaces en un objeto a un cliente a través de `QueryInterface`.  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase en que expone interfaces.  
  
### <a name="remarks"></a>Comentarios  
 [CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) sólo devuelve punteros para interfaces en el mapa COM. Iniciar la asignación de interfaz con el `BEGIN_COM_MAP` (macro), agregar entradas para cada una de las interfaces con el [COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5) macro o uno de sus variantes y complete la asignación con el [END_COM_MAP](#end_com_map) macro.  

  
### <a name="example"></a>Ejemplo  
 De ATL [BUSCAPERSONAS](../../visual-cpp-samples.md) ejemplo:  
  
 [!code-cpp[NVC_ATL_COM N.º&1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrymacrosa--cominterfaceentry-macros"></a><a name="com_interface_entry_macros"></a>Macros COM_INTERFACE_ENTRY  
 Estas macros escriba interfaces de un objeto en su mapa COM para que sean accesibles para `QueryInterface`. El orden de las entradas en el mapa COM es las interfaces de orden se comprobará para hallar una coincidencia **IID** durante `QueryInterface`.  
  
##  <a name="a-namecominterfaceentry2x2a--cominterfaceentry2"></a><a name="com_interface_entry2_x2"></a>COM_INTERFACE_ENTRY2  
 Utilice esta macro para eliminar la ambigüedad entre dos ramas de la herencia.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de una interfaz que desea exponer desde el objeto.  
  
 `x2`  
 [in] El nombre de la bifurcación de herencia desde la que *x* se expone.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si se deriva el objeto de clase desde dos interfaces duales, exponer `IDispatch` con `COM_INTERFACE_ENTRY2` desde `IDispatch` puede obtenerse desde cualquiera de las interfaces.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryiida--cominterfaceentryiid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID  
 Use esta macro para entrar en la interfaz en el mapa COM y especificar su IID.  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz expuesta.  
  
 *x*  
 [in] El nombre de la clase cuyo vtable se expondrá como la interfaz identificada por `iid`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#117;](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="a-namecominterfaceentry2iida--cominterfaceentry2iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID  
 Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), salvo que puede especificar un IID diferentes.  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID que especifica para la interfaz.  
  
 *x*  
 [in] El nombre de una interfaz que su objeto de clase se deriva directamente.  
  
 `x2`  
 [in] El nombre de una segunda interfaz que su objeto de clase se deriva directamente.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentry2a--cominterfaceentry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2  
 Utilice esta macro para eliminar la ambigüedad entre dos ramas de la herencia.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de una interfaz que desea exponer desde el objeto.  
  
 `x2`  
 [in] El nombre de la bifurcación de herencia desde la que *x* se expone.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si se deriva el objeto de clase desde dos interfaces duales, exponer `IDispatch` con `COM_INTERFACE_ENTRY2` desde `IDispatch` puede obtenerse desde cualquiera de las interfaces.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryaggregate2a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate2"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 Cuando la interfaz identificado por `iid` se consulta, `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz de consulta.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero.  
  
### <a name="remarks"></a>Comentarios  
 El `punk` se supone que el parámetro para que apunte a lo desconocido interno de un agregado o a **NULL**, en cuyo caso se omite la entrada. Normalmente, lo haría **CoCreate** el agregado en `FinalConstruct`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryaggregateblinda--cominterfaceentryaggregateblind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), salvo que consultar los IID da como resultado la consulta de reenvío `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>Parámetros  
 `punk`  
 [in] El nombre de un **IUnknown** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la consulta de la interfaz, el procesamiento de la asignación COM continúa.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#113;](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  
##  <a name="a-namecominterfaceentryaggregate3a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate3"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 Cuando la interfaz identificado por `iid` se consulta, `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz de consulta.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero.  
  
### <a name="remarks"></a>Comentarios  
 El `punk` se supone que el parámetro para que apunte a lo desconocido interno de un agregado o a **NULL**, en cuyo caso se omite la entrada. Normalmente, lo haría **CoCreate** el agregado en `FinalConstruct`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregatea--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si `punk` es **NULL**, crea automáticamente el agregado descrito por el `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz de consulta.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero. Debe ser un miembro de la clase que contiene la asignación COM.  
  
 `clsid`  
 [in] El identificador de la función de agregado que se creará si `punk` es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentryaggregatea--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 Cuando la interfaz identificado por `iid` se consulta, `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz de consulta.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero.  
  
### <a name="remarks"></a>Comentarios  
 El `punk` se supone que el parámetro para que apunte a lo desconocido interno de un agregado o a **NULL**, en cuyo caso se omite la entrada. Normalmente, lo haría **CoCreate** el agregado en `FinalConstruct`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregateblinda--cominterfaceentryautoaggregateblind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), salvo que consultar los IID da como resultado la consulta de reenvío `punk`y si `punk` es **NULL**, automáticamente crea el agregado descrito por el `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>Parámetros  
 `punk`  
 [in] El nombre de un **IUnknown** puntero. Debe ser un miembro de la clase que contiene la asignación COM.  
  
 `clsid`  
 [in] El identificador de la función de agregado que se creará si `punk` es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la consulta de la interfaz, el procesamiento de la asignación COM continúa.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#115;](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregate2a--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate2"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si `punk` es **NULL**, crea automáticamente el agregado descrito por el `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz de consulta.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero. Debe ser un miembro de la clase que contiene la asignación COM.  
  
 `clsid`  
 [in] El identificador de la función de agregado que se creará si `punk` es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentrybreaka--cominterfaceentrybreak"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK  
 Hace que el programa llamar a [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) cuando se consulta la interfaz especificada.  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Texto utilizado para construir el identificador de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz se construirá el IID anexando *x* a `IID_`. Por ejemplo, si *x* es `IPersistStorage`, será el IID `IID_IPersistStorage`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentrycachedtearoffa--cominterfaceentrycachedtearoff"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 Guarda los datos de la interfaz específica para cada instancia.  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz desplazable.  
  
 *x*  
 [in] El nombre de la clase que implementa la interfaz.  
  
 `punk`  
 [in] El nombre de un **IUnknown** puntero. Debe ser un miembro de la clase que contiene la asignación COM. Se debe inicializar para **NULL** en el constructor del objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 Si no se usa la interfaz, esto reduce el tamaño total de la instancia del objeto.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#54;](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="a-namecominterfaceentrytearoffa--cominterfaceentrytearoff"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF  
 Expone las interfaces divisibles.  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz desplazable.  
  
 *x*  
 [in] El nombre de la clase que implementa la interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Una interfaz desplazable se implementa como un objeto independiente que se crea una instancia cada vez que representa la interfaz se consulta. Normalmente, compile la interfaz como un desplazable si apenas se usa la interfaz, ya que esto guarda un puntero vtable en cada instancia del objeto principal. El desplazable se eliminará cuando su recuento de referencias se convierte en cero. La clase que implementa el desplazable debe derivarse de `CComTearOffObjectBase` y tienen su propio mapa COM.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM N.º&1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrychaina--cominterfaceentrychain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN  
 Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>Parámetros  
 *nombre de clase*  
 [in] Una clase base del objeto actual.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, en el código siguiente:  
  
 [!code-cpp[NVC_ATL_Windowing&#116;](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 Tenga en cuenta que la primera entrada en el mapa COM debe ser una interfaz en el objeto que contiene la asignación COM. Por lo tanto, no se puede iniciar las entradas de mapa COM con `COM_INTERFACE_ENTRY_CHAIN`, lo que hace que el mapa COM de un objeto diferente que se buscará en el punto donde **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** aparece en el mapa de COM del objeto. Si desea buscar el mapa COM de otro objeto en primer lugar, agregue una entrada de la interfaz para **IUnknown** al mapa COM, a continuación, encadenar mapa de COM de otro objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing&#111;](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentryfunc2a--cominterfaceentryfunc"></a><a name="com_interface_entry_func2"></a>COM_INTERFACE_ENTRY_FUNC  
 Un mecanismo general para enlazar con ATL `QueryInterface` lógica.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz expuesta.  
  
 `dw`  
 [in] Pasa un parámetro a la `func`.  
  
 `func`  
 [in] El puntero de función devolverá `iid`.  
  
### <a name="remarks"></a>Comentarios  
 Si *iid* coincide con el IID de la interfaz de consulta y, a continuación, la función especificada por `func` se llama. La declaración de la función debe ser:  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Cuando se llama a la función, `pv` apunta a su objeto de clase. El `riid` parámetro hace referencia a la interfaz que se está consultando, `ppv` es el puntero a la ubicación donde la función debe almacenar el puntero a la interfaz, y `dw` es el parámetro especificado en la entrada. Debe establecer la función \* `ppv` a **NULL** y devolver **E_NOINTERFACE** o **S_FALSE** si elige no devuelven una interfaz. Con **E_NOINTERFACE**, procesamiento de mapa COM finaliza. Con **S_FALSE**, continúa el procesamiento de asignación COM, aunque no devolvió ningún puntero de interfaz. Si la función devuelve un puntero de interfaz, debe devolver `S_OK`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentryfuncblinda--cominterfaceentryfuncblind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND  
 Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), salvo que consultar los IID da como resultado una llamada a `func`.  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>Parámetros  
 `dw`  
 [in] Pasa un parámetro a la `func`.  
  
 `func`  
 [in] La función que se llama cuando se procesa esta entrada en el mapa COM.  
  
### <a name="remarks"></a>Comentarios  
 Cualquier error hará que el procesamiento continúe en el mapa COM. Si la función devuelve un puntero de interfaz, debe devolver `S_OK`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentryfunca--cominterfaceentryfunc"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC  
 Un mecanismo general para enlazar con ATL `QueryInterface` lógica.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz expuesta.  
  
 `dw`  
 [in] Pasa un parámetro a la `func`.  
  
 `func`  
 [in] El puntero de función devolverá `iid`.  
  
### <a name="remarks"></a>Comentarios  
 Si *iid* coincide con el IID de la interfaz de consulta y, a continuación, la función especificada por `func` se llama. La declaración de la función debe ser:  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Cuando se llama a la función, `pv` apunta a su objeto de clase. El `riid` parámetro hace referencia a la interfaz que se está consultando, `ppv` es el puntero a la ubicación donde la función debe almacenar el puntero a la interfaz, y `dw` es el parámetro especificado en la entrada. Debe establecer la función \* `ppv` a **NULL** y devolver **E_NOINTERFACE** o **S_FALSE** si elige no devuelven una interfaz. Con **E_NOINTERFACE**, procesamiento de mapa COM finaliza. Con **S_FALSE**, continúa el procesamiento de asignación COM, aunque no devolvió ningún puntero de interfaz. Si la función devuelve un puntero de interfaz, debe devolver `S_OK`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-namecominterfaceentrynointerfacea--cominterfaceentrynointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE  
 Devuelve **E_NOINTERFACE** y finaliza el procesamiento de mapa COM cuando se consulta la interfaz especificada.  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Texto utilizado para construir el identificador de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar esta macro para evitar que una interfaz se usa en un caso concreto. Por ejemplo, puede insertar esta macro en su COM justo antes de asignar `COM_INTERFACE_ENTRY_AGGREGATE_BLIND` para impedir que una consulta para la interfaz se reenvían al desconocido interno del agregado.  
  
 La interfaz se construirá el IID anexando *x* a `IID_`. Por ejemplo, si *x* es `IPersistStorage`, será el IID `IID_IPersistStorage`.  
  
 Consulte [Macros COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) para comentarios sobre COM entradas del mapa.  
  
##  <a name="a-nameendcommapa--endcommap"></a><a name="end_com_map"></a>END_COM_MAP  
 Termina la definición de la asignación de interfaz COM.  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de mapa COM](../../atl/reference/com-map-global-functions.md)

