---
title: "Macros de categoría | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs: C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 752a0c0c9de5c726a106ca08a574844369c6bdc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="category-macros"></a>Macros de categoría
Estas macros definen asignaciones de categoría.  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marca el principio de la asignación de categoría.|  
|[END_CATEGORY_MAP](#end_category_map)|Marca el final de la asignación de categoría.|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indica categorías implementadas por el objeto COM.|  
|[REQUIRED_CATEGORY](#required_category)|Indica las categorías que se necesitan del contenedor por el objeto COM.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 Marca el principio de la asignación de categoría.  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] El nombre de la clase que contiene la asignación de categoría.  
  
### <a name="remarks"></a>Comentarios  
 La asignación de categoría se usa para especificar qué categorías del componente implementará la clase COM y qué categorías requiere de su contenedor.  
  
 Agregar un [IMPLEMENTED_CATEGORY](#implemented_category) entrada a la asignación para cada categoría de implementada por la clase COM. Agregar un [REQUIRED_CATEGORY](#required_category) entrada a la asignación para cada categoría de la clase requiere que sus clientes implementar. Marcar el final de la asignación con el [END_CATEGORY_MAP](#end_category_map) macro.  
  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociado un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .  
  
> [!NOTE]
>  ATL usa el Administrador de categorías del componente estándar para registrar categorías del componente. Si el administrador no está presente en el sistema cuando se registra el módulo, el registro se realiza correctamente, pero las categorías de componente no se registrará para esa clase.  
  
 Para obtener más información acerca de las categorías de componente, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) del SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>END_CATEGORY_MAP  
 Marca el final de la asignación de categoría.  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_CATEGORY_MAP](#begin_category_map).  
  
##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 Agregar un `IMPLEMENTED_CATEGORY` macro para el componente [mapa de categoría de](#begin_category_map) para especificar que se debe registrar como implementación de la categoría identificada por la `catID` parámetro.  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>Parámetros  
 `catID`  
 [in] A **CATID** constante o variable que contiene el identificador único global (GUID) para la categoría de implementada. La dirección de `catID` se realiza y se agrega al mapa. Consulte la tabla siguiente para una serie de categorías estándar.  
  
### <a name="remarks"></a>Comentarios  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociado un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.  
  
 Los clientes pueden utilizar la información de categoría registrada para la clase para determinar sus requisitos y capacidades sin tener que crear una instancia del mismo.  
  
 Para obtener más información acerca de las categorías de componente, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) del SDK de Windows.  
  
### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de cotizaciones  
  
|Descripción|Símbolo|GUID de registro|  
|-----------------|------------|-------------------|  
|Seguro para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objetos orientados a Internet|Vea [objetos compatibles con Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) en el SDK de Windows para obtener una lista de ejemplo.||  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>REQUIRED_CATEGORY  
 Agregar un `REQUIRED_CATEGORY` macro para el componente [mapa de categoría de](#begin_category_map) para especificar que se debe registrar que requieran la categoría identificada por la `catID` parámetro.  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>Parámetros  
 `catID`  
 [in] A **CATID** constante o variable que contiene el identificador único global (GUID) para la categoría necesaria. La dirección de `catID` se realiza y se agrega al mapa. Consulte la tabla siguiente para una serie de categorías estándar.  
  
### <a name="remarks"></a>Comentarios  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociado un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.  
  
 Los clientes pueden utilizar la información de categoría registrada para la clase para determinar sus requisitos y capacidades sin tener que crear una instancia del mismo. Por ejemplo, un control puede requerir que un contenedor admiten el enlace de datos. El contenedor puede averiguar si tiene las capacidades necesarias hospedar el control al consultar el Administrador de categoría para las categorías requeridas por dicho control. Si el contenedor no admite una característica necesaria, puede rechazar hospedar el objeto COM.  
  
 Para obtener más información acerca de las categorías de componentes, incluida una lista de ejemplo, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) del SDK de Windows.  
  
### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de cotizaciones  
  
|Descripción|Símbolo|GUID de registro|  
|-----------------|------------|-------------------|  
|Seguro para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objetos orientados a Internet|Vea [objetos compatibles con Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) en el SDK de Windows para obtener una lista de ejemplo.||  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
