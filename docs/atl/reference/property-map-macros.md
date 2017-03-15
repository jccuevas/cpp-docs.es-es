---
title: Macros de mapa de propiedades | Documentos de Microsoft
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
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fbbed22766f9029456f15c4a554ae91322e6a275
ms.lasthandoff: 02/24/2017

---
# <a name="property-map-macros"></a>Macros de mapa de propiedades
Estas macros definen entradas y mapas de propiedades.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca el comienzo de la asignación de propiedades ATL.|  
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica la medida o dimensiones de un control ActiveX.|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|Escribe una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en la asignación de propiedad.|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Escribe una descripción de propiedad, la propiedad DISPID, CLSID, de página de propiedades y `IDispatch` IID en la asignación de propiedad.|  
|[PROP_PAGE](#prop_page)|Escribe una página de propiedades CLSID en la asignación de propiedad.|  
|[END_PROP_MAP](#end_prop_map)|Marca el final de la asignación de propiedades ATL.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="a-namebeginpropmapa--beginpropmap"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 Marca el comienzo de la asignación de propiedad del objeto.  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] Especifica la clase que contiene la asignación de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La asignación de propiedad almacena las descripciones de propiedad, propiedad DISPID, CLSID, de página de propiedades y `IDispatch` IID. Clases de [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), y [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) utilizar la asignación de propiedad para recuperar y establecer esta información.  
  
 Cuando se crea un objeto con el Asistente para proyectos ATL, el asistente creará una asignación de propiedad vacío especificando `BEGIN_PROP_MAP` seguido [END_PROP_MAP](#end_prop_map).  
  
 `BEGIN_PROP_MAP`No guardar la extensión (es decir, las dimensiones) de una asignación de propiedad, porque un objeto usando una asignación de propiedad no puede tener una interfaz de usuario, por lo que no tendría ninguna extensión. Si el objeto es un control ActiveX con una interfaz de usuario, tiene una extensión. En este caso, debe especificar [PROP_DATA_ENTRY](#prop_data_entry) en la asignación de propiedad para proporcionar la medida.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#103;](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="a-namepropdataentrya--propdataentry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 Indica la medida o dimensiones de un control ActiveX.  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `member`  
 [in] El miembro de datos que contiene la extensión; Por ejemplo, `m_sizeExtent`.  
  
 *VT*  
 [in] Especifica el tipo de variante de la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro hace que el miembro de datos especificado se debe almacenar.  
  
 Cuando se crea un control ActiveX, el asistente inserta esta macro después de la macro de mapa de propiedades [BEGIN_PROP_MAP](#begin_prop_map) y antes de la macro de mapa de propiedades [END_PROP_MAP](#end_prop_map).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la extensión del objeto ( `m_sizeExtent`) es que se conserva.  
  
 [!code-cpp[NVC_ATL_Windowing&#131;](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing&#132;](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="a-namepropentrytypea--propentrytype"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 Use esta macro para escribir una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en la asignación de propiedad del objeto.  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `dispid`  
 [in] DISPID de la propiedad.  
  
 `clsid`  
 [in] El CLSID de la página de propiedades asociada. Utilice el valor especial `CLSID_NULL` para una propiedad que no tiene una página de propiedades asociadas.  
  
 `vt`  
 [in] El tipo de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 El `PROP_ENTRY` macro era inseguro y obsoleto. Se ha reemplazado por `PROP_ENTRY_TYPE`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el comienzo de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).  
  
##  <a name="a-namepropentrytypeexa--propentrytypeex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 Similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero permite especificar un IID determinado si su objeto admite varias interfaces duales.  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `dispid`  
 [in] DISPID de la propiedad.  
  
 `clsid`  
 [in] El CLSID de la página de propiedades asociada. Utilice el valor especial `CLSID_NULL` para una propiedad que no tiene una página de propiedades asociadas.  
  
 `iidDispatch`  
 [in] El IID de la definición de la propiedad de interfaz dual.  
  
 `vt`  
 [in] El tipo de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 El `PROP_ENTRY_EX` macro era inseguro y obsoleto. Se ha reemplazado por `PROP_ENTRY_TYPE_EX`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el comienzo de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se agrupan las entradas de `IMyDual1` seguido de una entrada para `IMyDual2`. La agrupación por interfaz dual mejorará el rendimiento.  
  
 [!code-cpp[NVC_ATL_Windowing&#133;](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="a-nameproppagea--proppage"></a><a name="prop_page"></a>PROP_PAGE  
 Use esta macro para especificar una página de propiedades CLSID en la asignación de propiedad del objeto.  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] El CLSID de una página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 `PROP_PAGE`es similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero no se requiere una descripción de la propiedad o el DISPID.  
  
> [!NOTE]
>  Si ya ha escrito un CLSID con `PROP_ENTRY_TYPE` o [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), no es necesario realizar una entrada adicional con `PROP_PAGE`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el comienzo de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#134;](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="a-nameendpropmapa--endpropmap"></a><a name="end_prop_map"></a>END_PROP_MAP  
 Marca el final de la asignación de propiedad del objeto.  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto con el Asistente para proyectos ATL, el asistente creará una asignación de propiedad vacío especificando [BEGIN_PROP_MAP](#begin_prop_map) seguido de `END_PROP_MAP`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

