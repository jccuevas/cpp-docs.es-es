---
title: Clase CTooltipManager
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
ms.openlocfilehash: 4e721740fc100a34ea08dd7ff5f9291eea2d9b36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752170"
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

## <a name="remarks"></a>Observaciones

Use [CMFCToolTipCtrl (Clase)](../../mfc/reference/cmfctooltipctrl-class.md)y `CMFCToolTipInfo` `CTooltipManager` juntos para implementar información sobre herramientas personalizada en la aplicación. Para obtener un ejemplo de cómo utilizar estas clases de información sobre herramientas, vea el [CMFCToolTipCtrl tema.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtooltipmanager.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::CreateToolTip

Crea un control de información sobre herramientas.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parámetros

*pToolTip*<br/>
[fuera] Una referencia a un puntero de información sobre herramientas. Se establece para que apunte a la información sobre herramientas recién creada cuando se devuelve la función.

*pWndParent*<br/>
[en] Padre de la información sobre herramientas.

*nType*<br/>
[en] Tipo de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha creado correctamente una información sobre herramientas.

### <a name="remarks"></a>Observaciones

Debe llamar a [CTooltipManager::DeleteToolTip](#deletetooltip) para eliminar el control de información sobre herramientas que se devuelve en *pToolTip*.

El [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) establece los parámetros de visualización visual de cada información sobre herramientas que crea en función del tipo de información sobre herramientas que *nType* especifica. Para cambiar los parámetros de uno o varios tipos de información sobre herramientas, llame a [CTooltipManager::SetTooltipParams](#settooltipparams).

Los tipos de información sobre herramientas válidos se enumeran en la tabla siguiente:

|Tipo de información sobre herramientas|Categoría de control|Tipos de ejemplo|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Un botón.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Una barra de subtítulos.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Cualquier control que no se ajuste a otra categoría.|Ninguno.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Un panel acoplable.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Cuadro de texto.|Ninguno.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Un minimarco.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Un planificador.|Ninguno.|
|AFX_TOOLTIP_TYPE_RIBBON|Una barra de cinta.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Un control de tabulación.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Una barra de herramientas.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Una caja de herramientas.|Ninguno.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip

Elimina el control de información sobre herramientas.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parámetros

*pToolTip*<br/>
[adentro, fuera] Una referencia a un puntero a una información sobre herramientas que se va a destruir.

### <a name="remarks"></a>Observaciones

Llame a este método para cada [CToolTipCtrl clase](../../mfc/reference/ctooltipctrl-class.md) creada por [CTooltipManager::CreateToolTip](#createtooltip). El control primario debe llamar `OnDestroy` a este método desde su controlador. Esto es necesario para quitar correctamente la información sobre herramientas del marco de trabajo. Este método establece *pToolTip* en NULL antes de que se devuelva.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams

Personaliza la apariencia del control de información sobre herramientas para los tipos de control de Windows especificados.

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parámetros

*nTipos*<br/>
[en] Especifica los tipos de control.

*pRTC*<br/>
[en] Clase en tiempo de ejecución de información sobre herramientas personalizada.

*pParams*<br/>
[en] Parámetros de información sobre herramientas.

### <a name="remarks"></a>Observaciones

Este método establece la clase en tiempo de ejecución y los parámetros iniciales que [el CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utiliza cuando crea información sobre herramientas. Cuando un control llama a [CTooltipManager::CreateToolTip](#createtooltip) y pasa un tipo de información sobre herramientas que es uno de los tipos indicados por *nTypes*, el administrador de información sobre herramientas crea un control de información sobre herramientas que es una instancia de la clase en tiempo de ejecución especificada por *pRTC* y pasa los parámetros especificados por *pParams* a la nueva información sobre herramientas.

Cuando se llama a este método, todos los propietarios de información sobre herramientas existentes reciben el mensaje de AFX_WM_UPDATETOOLTIPS y deben volver a crear sus descripciones emergentes mediante [CTooltipManager::CreateToolTip](#createtooltip).

*nTypes* puede ser cualquier combinación de los tipos de información sobre herramientas válidos que [CTooltipManager::CreateToolTip](#createtooltip) utiliza, o puede ser AFX_TOOLTIP_TYPE_ALL. Si pasa AFX_TOOLTIP_TYPE_ALL, todos los tipos de información sobre herramientas se verán afectados.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `SetTooltipParams` muestra `CTooltipManager` cómo utilizar el método de la clase. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText

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

*Pti*<br/>
[en] Puntero a un objeto TOOLINFO.

*pToolTip*<br/>
[adentro, fuera] Puntero al control de información sobre herramientas para el que se debe establecer el texto y la descripción.

*nType*<br/>
[en] Especifica el tipo de control con el que está asociada esta información sobre herramientas.

*strText*<br/>
[en] Texto que se establecerá como texto de información sobre herramientas.

*lpszDescr*<br/>
[en] Un puntero a la descripción de la información sobre herramientas. Puede ser NULL.

### <a name="remarks"></a>Observaciones

El valor de *nType* debe ser el mismo valor que el *nType* parámetro de [CTooltipManager::CreateToolTip](#createtooltip) al crear la información sobre herramientas.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl Clase](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo (Clase)](../../mfc/reference/cmfctooltipinfo-class.md)
