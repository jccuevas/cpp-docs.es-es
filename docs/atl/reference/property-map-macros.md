---
title: Macros de asignación de propiedad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 718028385b3910b955c49ab9e0abddf23b443967
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="property-map-macros"></a>Macros de asignación de propiedad
Estas macros definen asignaciones de propiedad y las entradas.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca el principio de la asignación de propiedad ATL.|  
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica la extensión o dimensiones, de un control ActiveX.|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|Escribe una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en la asignación de propiedad.|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Escribe una descripción de propiedad, la propiedad identificador DISPID, página de propiedades CLSID, y `IDispatch` IID en la asignación de propiedad.|  
|[PROP_PAGE](#prop_page)|Escribe una página de propiedades CLSID en la asignación de propiedad.|  
|[END_PROP_MAP](#end_prop_map)|Marca el final de la asignación de propiedad ATL.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP  
 Marca el principio de asignación de propiedad del objeto.  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] Especifica la clase que contiene la asignación de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La asignación de propiedad almacena las descripciones de propiedad, propiedad DISPID, página de propiedades CLSID, y `IDispatch` IID. Clases de [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), y [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)usar la asignación de propiedad para recuperar y establecer esta información.  
  
 Cuando se crea un objeto con el Asistente para proyectos ATL, el asistente creará una asignación de propiedad vacío especificando `BEGIN_PROP_MAP` seguido [END_PROP_MAP](#end_prop_map).  
  
 `BEGIN_PROP_MAP` No guardar la extensión (es decir, las dimensiones) de una asignación de propiedad, porque un objeto con una asignación de propiedad no puede tener una interfaz de usuario, por lo que no habría ninguna extensión. Si el objeto es un control ActiveX con una interfaz de usuario, tiene una extensión. En este caso, debe especificar [PROP_DATA_ENTRY](#prop_data_entry) en la asignación de propiedad para proporcionar la extensión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY  
 Indica la extensión o dimensiones, de un control ActiveX.  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `member`  
 [in] El miembro de datos que contiene la extensión; Por ejemplo, `m_sizeExtent`.  
  
 *vt*  
 [in] Especifica el tipo de variante de la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro hace que el miembro de datos especificado que se deben conservar.  
  
 Cuando se crea un control ActiveX, el asistente inserta esta macro después de la macro de asignación de propiedad [BEGIN_PROP_MAP](#begin_prop_map) y antes de la macro de asignación de propiedad [END_PROP_MAP](#end_prop_map).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la extensión del objeto ( `m_sizeExtent`) es el que se conserva.  
  
 [!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE  
 Utilice esta macro para escribir una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en asignación de propiedad del objeto.  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `dispid`  
 [in] DISPID de la propiedad.  
  
 `clsid`  
 [in] El CLSID de la página de propiedades asociado. Utilice el valor especial `CLSID_NULL` para una propiedad que no tiene una página de propiedades asociado.  
  
 `vt`  
 [in] El tipo de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 El `PROP_ENTRY` macro era inseguro y en desuso. Se ha reemplazado por `PROP_ENTRY_TYPE`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).  
  
##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX  
 Similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero le permite especificar un IID determinado si el objeto admite varias interfaces duales.  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>Parámetros  
 `szDesc`  
 [in] La descripción de la propiedad.  
  
 `dispid`  
 [in] DISPID de la propiedad.  
  
 `clsid`  
 [in] El CLSID de la página de propiedades asociado. Utilice el valor especial `CLSID_NULL` para una propiedad que no tiene una página de propiedades asociado.  
  
 `iidDispatch`  
 [in] El IID de la definición de la propiedad de interfaz dual.  
  
 `vt`  
 [in] El tipo de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 El `PROP_ENTRY_EX` macro era inseguro y en desuso. Se ha reemplazado por `PROP_ENTRY_TYPE_EX`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se agrupa las entradas de `IMyDual1` seguido de una entrada para `IMyDual2`. Agrupar por interfaz dual mejorará el rendimiento.  
  
 [!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="prop_page"></a>  PROP_PAGE  
 Use esta macro para especificar una página de propiedades CLSID en asignación de propiedad del objeto.  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] El CLSID de una página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 `PROP_PAGE` es similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero no requiere una descripción de la propiedad o el DISPID.  
  
> [!NOTE]
>  Si ya ha escrito un CLSID con `PROP_ENTRY_TYPE` o [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), no es necesario realizar una entrada adicional con `PROP_PAGE`.  
  
 El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; el [END_PROP_MAP](#end_prop_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="end_prop_map"></a>  END_PROP_MAP  
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
