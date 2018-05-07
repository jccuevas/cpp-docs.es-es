---
title: Clase CTooltipManager | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78b191766e33d291317ef50a4d5373dc26428577
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ctooltipmanager-class"></a>Clase CTooltipManager
Mantiene información de tiempo de ejecución sobre información sobre herramientas. La clase `CTooltipManager` se crea una vez por cada aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Crea un control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Elimina el control de información sobre herramientas.|  
|[Ctooltipmanager:: Settooltipparams](#settooltipparams)|Personaliza la apariencia visual del control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Establece el texto y la descripción para un control de información sobre herramientas.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Comentarios  
 Use [CMFCToolTipCtrl clase](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, y `CTooltipManager` juntos para implementar información sobre herramientas personalizada en la aplicación. Para obtener un ejemplo de cómo usar estas clases de información sobre herramientas, vea el [CMFCToolTipCtrl clase](../../mfc/reference/cmfctooltipctrl-class.md) tema.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip  
 Crea un control de información sobre herramientas.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pToolTip`  
 Una referencia a un puntero de información sobre herramientas. Se establece para que apunte a la información sobre herramientas recién creado cuando la función devuelve.  
  
 [in] `pWndParent`  
 Elemento primario de la información sobre herramientas.  
  
 [in] `nType`  
 Tipo de la información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha creado correctamente una información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a [CTooltipManager::DeleteToolTip](#deletetooltip) para eliminar el control de información sobre herramientas que se pasa en `pToolTip`.  
  
 El [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) establece los parámetros de presentación de cada información sobre herramientas crea basan en la información sobre herramientas de tipo que `nType` especifica. Para cambiar los parámetros de uno o más tipos de información sobre herramientas, llame a [ctooltipmanager:: Settooltipparams](#settooltipparams).  
  
 Los tipos válidos de información sobre herramientas se muestran en la tabla siguiente:  
  
|ToolTip (tipo)|Categoría de control|Ejemplos de tipos|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Un botón.|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Una barra de título.|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|Cualquier control que no se ajusta a otra categoría.|Ninguno.|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Un panel acoplable.|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|Un cuadro de texto.|Ninguno.|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Un marco reducido.|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|Un programador.|Ninguno.|  
|AFX_TOOLTIP_TYPE_RIBBON|Una barra de cinta.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|Un control de pestaña.|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Una barra de herramientas.|CMFCToolBar, CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Un cuadro de herramientas.|Ninguno.|  
  
##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip  
 Elimina el control de información sobre herramientas.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pToolTip`  
 Una referencia a un puntero a una información sobre herramientas al ser destruidos.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para cada [CToolTipCtrl (clase)](../../mfc/reference/ctooltipctrl-class.md) creado por [CTooltipManager::CreateToolTip](#createtooltip). El control primario debe llamar a este método desde su `OnDestroy` controlador. Esto es necesario para quitar correctamente la información sobre herramientas en el marco de trabajo. Este método establece `pToolTip` a `NULL` antes de regresar.  
  
##  <a name="settooltipparams"></a>  Ctooltipmanager:: Settooltipparams  
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
 Clase en tiempo de ejecución de información sobre herramientas personalizada.  
  
 [in] `pParams`  
 Parámetros de información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la clase en tiempo de ejecución y los parámetros iniciales que el [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) usa al crear información sobre herramientas. Cuando un control llama [CTooltipManager::CreateToolTip](#createtooltip) y pasa información sobre herramientas de tipo que es uno de los tipos que se indican por `nTypes`, el Administrador de información sobre herramientas crea un control de información sobre herramientas que es una instancia de la clase en tiempo de ejecución especificada por `pRTC` y pasa los parámetros especificados por `pParams` a la información sobre herramientas nuevo.  
  
 Cuando se llama a este método, todos los propietarios de información sobre herramientas existentes reciban el mensaje AFX_WM_UPDATETOOLTIPS y debe volver a crear su información sobre herramientas mediante el uso de [CTooltipManager::CreateToolTip](#createtooltip).  
  
 `nTypes` puede ser cualquier combinación de la información sobre herramientas válido tipos que [CTooltipManager::CreateToolTip](#createtooltip) utiliza, o puede ser AFX_TOOLTIP_TYPE_ALL. Si se pasa AFX_TOOLTIP_TYPE_ALL, se ven afectados todos los tipos de información sobre herramientas.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetTooltipParams` método de la `CTooltipManager` clase. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
 Establece el texto y una descripción para una información sobre herramientas.  
  
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
 Un puntero a un objeto TOOLINFO.  
  
 [in, out] `pToolTip`  
 Un puntero para el control de información sobre herramientas para el que se va a establecer el texto y la descripción.  
  
 [in] `nType`  
 Especifica el tipo de control al que está asociado este información sobre herramientas.  
  
 [in] `strText`  
 El texto que se establecerá como el texto de información sobre herramientas.  
  
 [in] `lpszDescr`  
 Un puntero a la descripción de la información sobre herramientas. Puede ser `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 El valor de `nType` debe ser el mismo valor que el `nType` parámetro de [CTooltipManager::CreateToolTip](#createtooltip) cuando creó la información sobre herramientas.  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo (clase)](../../mfc/reference/cmfctooltipinfo-class.md)
