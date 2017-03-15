---
title: "Macros de categoría | Documentos de Microsoft"
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
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
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
ms.openlocfilehash: 26eea5cc8ce8e18af84a9ca89e5ddc94272be44c
ms.lasthandoff: 02/24/2017

---
# <a name="category-macros"></a>Macros de categoría
Estas macros definen las asignaciones de categoría.  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marca el comienzo de la asignación de categoría.|  
|[END_CATEGORY_MAP](#end_category_map)|Marca el final de la asignación de categoría.|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indica las categorías que se implementan mediante el objeto COM.|  
|[REQUIRED_CATEGORY](#required_category)|Indica las categorías que se necesitan del contenedor por el objeto COM.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  

##  <a name="a-namebegincategorymapa--begincategorymap"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 Marca el comienzo de la asignación de categoría.  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] El nombre de la clase que contiene la asignación de categoría.  
  
### <a name="remarks"></a>Comentarios  
 La asignación de categoría se utiliza para especificar qué categorías del componente implementará la clase COM y las categorías que requiere de su contenedor.  
  
 Agregar una [IMPLEMENTED_CATEGORY](#implemented_category) entrada a la asignación de cada categoría de implementada por la clase COM. Agregar un [REQUIRED_CATEGORY](#required_category) entrada a la asignación para cada categoría de la clase requiere que sus clientes a implementar. Marcar el final de la asignación con el [END_CATEGORY_MAP](#end_category_map) (macro).  
  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).  
  
> [!NOTE]
>  ATL utiliza el Administrador de categorías de componentes estándar para registrar las categorías de componente. Si el administrador no está presente en el sistema cuando se registra el módulo, el registro se realiza correctamente, pero las categorías del componente no se registrará para esa clase.  
  
 Para obtener más información acerca de las categorías de componente, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing Nº&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="a-nameendcategorymapa--endcategorymap"></a><a name="end_category_map"></a>END_CATEGORY_MAP  
 Marca el final de la asignación de categoría.  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_CATEGORY_MAP](#begin_category_map).  
  
##  <a name="a-nameimplementedcategorya--implementedcategory"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 Agregar una `IMPLEMENTED_CATEGORY` macro a su componente [mapa de categoría de](#begin_category_map) para especificar que se debe registrar como implementación de la categoría identificada por la `catID` parámetro.  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>Parámetros  
 `catID`  
 [in] Un **CATID** constante o variable que contiene el identificador único global (GUID) para la categoría de implementada. La dirección de `catID` se toma y se agrega al mapa. Vea la tabla siguiente para ver una selección de categorías estándar.  
  
### <a name="remarks"></a>Comentarios  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.  
  
 Los clientes pueden utilizar la información de categoría registrada para la clase para determinar sus requisitos y funciones sin tener que crear una instancia de ella.  
  
 Para obtener más información acerca de las categorías de componente, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de acciones  
  
|Descripción|Símbolo|GUID del registro|  
|-----------------|------------|-------------------|  
|Seguro para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objetos orientados a Internet|Consulte [objetos de cuenta de Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de ejemplo.||  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing Nº&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="a-namerequiredcategorya--requiredcategory"></a><a name="required_category"></a>REQUIRED_CATEGORY  
 Agregar un `REQUIRED_CATEGORY` macro a su componente [mapa de categoría de](#begin_category_map) para especificar que se debe registrar como que requiere la categoría identificada por la `catID` parámetro.  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>Parámetros  
 `catID`  
 [in] Un **CATID** constante o variable que contiene el identificador único global (GUID) para la categoría requerida. La dirección de `catID` se toma y se agrega al mapa. Vea la tabla siguiente para ver una selección de categorías estándar.  
  
### <a name="remarks"></a>Comentarios  
 Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.  
  
 Los clientes pueden utilizar la información de categoría registrada para la clase para determinar sus requisitos y funciones sin tener que crear una instancia de ella. Por ejemplo, un control puede requerir que un contenedor admiten el enlace de datos. El contenedor puede averiguar si tiene las capacidades necesarias para hospedar el control consultando el Administrador de categoría para las categorías requeridas por dicho control. Si el contenedor no admite una característica necesaria, puede rechazar alojar el objeto COM.  
  
 Para obtener más información acerca de las categorías de componentes, incluida una lista de ejemplo, vea [¿qué categorías de componentes y cómo funcionan](http://msdn.microsoft.com/library/windows/desktop/ms694322) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de acciones  
  
|Descripción|Símbolo|GUID del registro|  
|-----------------|------------|-------------------|  
|Seguro para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objetos orientados a Internet|Consulte [objetos de cuenta de Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de ejemplo.||  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#135;](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

