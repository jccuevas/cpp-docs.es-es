---
title: Clase CTooltipManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager class
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3bbf191aacdd318f2afb0bd1a126c3eff290fad6
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ctooltipmanager-class"></a>Clase CTooltipManager
Mantiene información de tiempo de ejecución sobre información sobre herramientas. La clase `CTooltipManager` se crea una vez por cada aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Crea un control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Elimina el control de información sobre herramientas.|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Personaliza la apariencia visual del control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Establece el texto y la descripción para un control de información sobre herramientas.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Comentarios  
 Utilice [clase CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, y `CTooltipManager` conjuntamente para implementar personalizada de información sobre herramientas en la aplicación. Para obtener un ejemplo de cómo utilizar estas clases de información sobre herramientas, vea el [clase CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) tema.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>CTooltipManager::CreateToolTip  
 Crea un control de información sobre herramientas.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pToolTip`  
 Una referencia a un puntero de información sobre herramientas. Se establece para que apunte a la información sobre herramientas recién creado cuando se devuelve la función.  
  
 [in] `pWndParent`  
 Elemento primario de la información sobre herramientas.  
  
 [in] `nType`  
 Tipo de la información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha creado correctamente una información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a [CTooltipManager::DeleteToolTip](#deletetooltip) para eliminar el control de información sobre herramientas que se pasa en `pToolTip`.  
  
 El [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) establece los parámetros de presentación visual de cada información sobre herramientas crea en función de la información sobre herramientas que escriba `nType` especifica. Para cambiar los parámetros de uno o más tipos de información sobre herramientas, llame a [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
 Los tipos válidos de información sobre herramientas se muestran en la tabla siguiente:  
  
|ToolTip (tipo)|Categoría de control|Tipos de ejemplo|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Un botón.|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Una barra de título.|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|Cualquier control que no se ajusta a otra categoría.|Ninguno.|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Un panel acoplable.|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|Un cuadro de texto.|Ninguno.|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Un marco reducido.|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|Un programador.|Ninguno.|  
|AFX_TOOLTIP_TYPE_RIBBON|Una barra de la cinta de opciones.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|Un control de ficha.|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Barra de herramientas.|CMFCToolBar, CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Un cuadro de herramientas.|Ninguno.|  
  
##  <a name="deletetooltip"></a>CTooltipManager::DeleteToolTip  
 Elimina el control de información sobre herramientas.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pToolTip`  
 Una referencia a un puntero a una información sobre herramientas se destruya.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para cada [CToolTipCtrl (clase)](../../mfc/reference/ctooltipctrl-class.md) creado por [CTooltipManager::CreateToolTip](#createtooltip). El control primario debe llamar a este método desde su `OnDestroy` controlador. Esto es necesario para quitar correctamente la información sobre herramientas de framework. Este método establece `pToolTip` a `NULL` antes de devolver.  
  
##  <a name="settooltipparams"></a>CTooltipManager::SetTooltipParams  
 Personaliza la apariencia del control de información sobre herramientas para los tipos de control de Windows especificados.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTypes`  
 Especifica los tipos de control.  
  
 [in] `pRTC`  
 Clase en tiempo de ejecución de la información sobre herramientas personalizado.  
  
 [in] `pParams`  
 Parámetros de información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la clase en tiempo de ejecución y los parámetros iniciales que el [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utiliza al crear información sobre herramientas. Cuando un control llama [CTooltipManager::CreateToolTip](#createtooltip) y pasa información sobre herramientas tipo que es uno de los tipos indicados por `nTypes`, el Administrador de información sobre herramientas crea un control de información sobre herramientas es una instancia de la clase en tiempo de ejecución especificada por `pRTC` y pasa los parámetros especificados por `pParams` a la información sobre herramientas nuevas.  
  
 Cuando se llama a este método, todos los propietarios existentes de información sobre herramientas reciben el mensaje AFX_WM_UPDATETOOLTIPS y debe volver a crear su información sobre herramientas mediante [CTooltipManager::CreateToolTip](#createtooltip).  
  
 `nTypes`puede ser cualquier combinación de la información sobre herramientas válido tipos que [CTooltipManager::CreateToolTip](#createtooltip) utiliza, o puede ser AFX_TOOLTIP_TYPE_ALL. Si se pasa AFX_TOOLTIP_TYPE_ALL, todos los tipos de información sobre herramientas se ven afectados.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetTooltipParams` método de la `CTooltipManager` clase. Este fragmento de código forma parte de la [ejemplo dibujar cliente](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient&#11;](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>CTooltipManager::SetTooltipText  
 Establece el texto y la descripción de una información sobre herramientas.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTI`  
 Puntero a un objeto TOOLINFO.  
  
 [in, out] `pToolTip`  
 Un puntero al control de información sobre herramientas para el que se establece el texto y la descripción.  
  
 [in] `nType`  
 Especifica el tipo de control al que está asociada esta información sobre herramientas.  
  
 [in] `strText`  
 El texto que se establecerá como el texto de información sobre herramientas.  
  
 [in] `lpszDescr`  
 Puntero a la descripción de la información sobre herramientas. Puede ser `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 El valor de `nType` debe ser el mismo valor que la `nType` parámetro de [CTooltipManager::CreateToolTip](#createtooltip) cuando creó la información sobre herramientas.  
  
##  <a name="updatetooltips"></a>CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)   
 [Clase CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

