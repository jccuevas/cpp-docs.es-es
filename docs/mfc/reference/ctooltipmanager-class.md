---
title: CTooltipManager (clase)
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 7ca0c657872bb2a3c56c9406a88f8c674cb46938
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260639"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager (clase)

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
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Personaliza la apariencia visual del control de información sobre herramientas para el tipo de control de Windows especificado.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Establece el texto y la descripción para un control de información sobre herramientas.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Comentarios

Use [CMFCToolTipCtrl (clase)](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, y `CTooltipManager` juntos para implementar información sobre herramientas personalizada en la aplicación. Para obtener un ejemplo de cómo utilizar estas clases de información sobre herramientas, vea el [CMFCToolTipCtrl (clase)](../../mfc/reference/cmfctooltipctrl-class.md) tema.

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

*pToolTip*<br/>
[out] Una referencia a un puntero de la información sobre herramientas. Se establece para que apunte a la información sobre herramientas recién creado cuando se devuelve la función.

*pWndParent*<br/>
[in] Elemento primario de la información sobre herramientas.

*nType*<br/>
[in] Tipo de la información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha creado correctamente una información sobre herramientas.

### <a name="remarks"></a>Comentarios

Debe llamar a [CTooltipManager::DeleteToolTip](#deletetooltip) para eliminar el control de información sobre herramientas que se pasa en *pToolTip*.

El [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) establece los parámetros de la presentación visual de cada información sobre herramientas crea en función de la información sobre herramientas que escriba *nLas* especifica. Para cambiar los parámetros para uno o varios tipos de información sobre herramientas, llame a [ctooltipmanager:: Settooltipparams](#settooltipparams).

Los tipos válidos de información sobre herramientas se muestran en la tabla siguiente:

|Tipo de información sobre herramientas|Categoría de control|Ejemplos de tipos|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Un botón.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Una barra de título.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Cualquier control que no se ajusta a otra categoría.|Ninguno.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Un panel acoplable.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Un cuadro de texto.|Ninguno.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Un marco reducido.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Una herramienta de planeación.|Ninguno.|
|AFX_TOOLTIP_TYPE_RIBBON|Una barra de cinta.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Un control de ficha.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Una barra de herramientas.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Un cuadro de herramientas.|Ninguno.|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

Elimina el control de información sobre herramientas.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parámetros

*pToolTip*<br/>
[in, out] Una referencia a un puntero a una información sobre herramientas que se va a destruir.

### <a name="remarks"></a>Comentarios

Llame a este método para cada [CToolTipCtrl (clase)](../../mfc/reference/ctooltipctrl-class.md) creado por [CTooltipManager::CreateToolTip](#createtooltip). El control primario debe llamar a este método desde su `OnDestroy` controlador. Esto es necesario para quitar correctamente la información sobre herramientas del marco de trabajo. Este método establece *pToolTip* en NULL antes de devolver.

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

Personaliza la apariencia del control de información sobre herramientas para los tipos de control de Windows especificados.

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parámetros

*nTypes*<br/>
[in] Especifica los tipos de control.

*pRTC*<br/>
[in] Clase en tiempo de ejecución de la información sobre herramientas personalizada.

*pParams*<br/>
[in] Parámetros de información sobre herramientas.

### <a name="remarks"></a>Comentarios

Este método establece la clase en tiempo de ejecución y los parámetros iniciales que el [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utiliza al crear información sobre herramientas. Cuando llama un control [CTooltipManager::CreateToolTip](#createtooltip) y pasa en una información sobre herramientas de tipo que es uno de los tipos indicados por *nTypes*, el Administrador de información sobre herramientas crea un control de información sobre herramientas que es una instancia de la clase en tiempo de ejecución especificada por *pRTC* y pasa los parámetros especificados por *pParams* para el nuevo objeto tooltip.

Cuando se llama a este método, todos los propietarios de información sobre herramientas existente reciben el mensaje AFX_WM_UPDATETOOLTIPS y debe volver a crear su información sobre herramientas mediante el uso de [CTooltipManager::CreateToolTip](#createtooltip).

*nTypes* puede ser cualquier combinación de la información sobre herramientas válido tipos que [CTooltipManager::CreateToolTip](#createtooltip) utiliza, o puede ser AFX_TOOLTIP_TYPE_ALL. Si se pasa AFX_TOOLTIP_TYPE_ALL, todos los tipos de información sobre herramientas se ven afectados.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `SetTooltipParams` método de la `CTooltipManager` clase. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../visual-cpp-samples.md).

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

*pTI*<br/>
[in] Un puntero a un objeto TOOLINFO.

*pToolTip*<br/>
[in, out] Un puntero al control de información sobre herramientas para el que se va a establecer el texto y la descripción.

*nType*<br/>
[in] Especifica el tipo de control que está asociada esta información sobre herramientas.

*strText*<br/>
[in] Texto que se establece como el texto de información sobre herramientas.

*lpszDescr*<br/>
[in] Un puntero a la descripción de la información sobre herramientas. Puede ser NULL.

### <a name="remarks"></a>Comentarios

El valor de *nLas* debe ser el mismo valor que el *nLas* parámetro de [CTooltipManager::CreateToolTip](#createtooltip) cuando creó la información sobre herramientas.

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
void UpdateTooltips();
```

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl (clase)](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo (clase)](../../mfc/reference/cmfctooltipinfo-class.md)
