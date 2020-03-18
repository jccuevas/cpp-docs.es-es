---
title: CBaseTabbedPane (clase)
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424606"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane (clase)

Extiende la funcionalidad de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) para permitir la creación de ventanas con pestañas.

## <a name="syntax"></a>Sintaxis

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTabbedPane:: AddTab](#addtab)|Agrega una nueva pestaña a un panel con pestañas.|
|[CBaseTabbedPane:: AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con pestañas vacío.|
|[CBaseTabbedPane:: ApplyRestoredTabInfo](#applyrestoredtabinfo)|Aplica la configuración de tabulación, que se carga desde el registro, a un panel con pestañas.|
|[CBaseTabbedPane:: CanFloat](#canfloat)|Determina si el panel puede flotar. (Invalida [a cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)).|
|[CBaseTabbedPane:: CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título del panel con pestañas debe mostrar el mismo texto que la pestaña activa.|
|[CBaseTabbedPane:: ConvertToTabbedDocument](#converttotabbeddocument)|(Invalida [CDockablePane:: ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)).|
|[CBaseTabbedPane::D etachPane](#detachpane)|Convierte uno o más paneles acoplables en documentos con pestañas MDI.|
|[CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Habilita o deshabilita la capacidad del panel con pestañas para sincronizar el texto del título con el texto de la etiqueta en la pestaña activa.|
|[CBaseTabbedPane:: FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaura el orden de tabulación interno a un estado predeterminado.|
|[CBaseTabbedPane:: FindBarByTabNumber](#findbarbytabnumber)|Devuelve un panel que reside en una pestaña cuando la ficha se identifica mediante un índice de tabulación basado en cero.|
|||
|[CBaseTabbedPane:: FindPaneByID](#findpanebyid)|Devuelve un panel que se identifica mediante el identificador del panel.|
|[CBaseTabbedPane:: FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.|
|[CBaseTabbedPane:: GetDefaultTabsOrder](#getdefaulttabsorder)|Devuelve el orden predeterminado de las fichas en el panel.|
|[CBaseTabbedPane:: GetFirstVisibleTab](#getfirstvisibletab)|Recupera un puntero a la primera pestaña mostrada.|
|[CBaseTabbedPane:: GetMinSize](#getminsize)|Recupera el tamaño mínimo permitido para el panel. (Invalida [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize)).|
|[CBaseTabbedPane:: GetPaneIcon](#getpaneicon)|Devuelve un identificador para el icono de panel. (Invalida [a cbasepane:: GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)).|
|[CBaseTabbedPane:: GetPaneList](#getpanelist)|Devuelve una lista de paneles contenidos en el panel con pestañas.|
|[CBaseTabbedPane:: GetTabArea](#gettabarea)|Devuelve los rectángulos delimitadores para las áreas de la pestaña superior e inferior.|
|[CBaseTabbedPane:: GetTabsNum](#gettabsnum)|Devuelve el recuento de pestañas de una ventana de pestaña.|
|[CBaseTabbedPane:: GetUnderlyingWindow](#getunderlyingwindow)|Obtiene la ventana de pestaña subyacente (ajustada).|
|[CBaseTabbedPane:: GetVisibleTabsNum](#getvisibletabsnum)|Devuelve el recuento de pestañas mostradas.|
|[CBaseTabbedPane:: HasAutoHideMode](#hasautohidemode)|Determina si el panel con pestañas se puede cambiar al modo de ocultación automática.|
|[CBaseTabbedPane:: IsHideSingleTab](#ishidesingletab)|Determina si el panel con pestañas está oculto si solo se muestra una pestaña.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Se utiliza internamente durante la serialización.|
|[CBaseTabbedPane:: RecalcLayout](#recalclayout)|Vuelve a calcular la información de diseño del panel. (Invalida [CPane:: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)).|
|[CBaseTabbedPane:: RemovePane](#removepane)|Quita un panel del panel con pestañas.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Se utiliza internamente durante la serialización.|
|`CBaseTabbedPane::Serialize`|(Invalida [CDockablePane:: Serialize](cdockablepane-class.md)).|
|`CBaseTabbedPane::SerializeTabWindow`|Se utiliza internamente durante la serialización.|
|[CBaseTabbedPane:: SetAutoDestroy](#setautodestroy)|Determina si la barra de control con pestañas se destruirá automáticamente.|
|[CBaseTabbedPane:: SetAutoHideMode](#setautohidemode)|Alterna el panel de acoplamiento entre el modo mostrado y el modo de ocultación automática. (Invalida [CDockablePane:: SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)).|
|[CBaseTabbedPane:: ShowTab](#showtab)|Muestra u oculta una pestaña.|

## <a name="remarks"></a>Observaciones

Esta clase es una clase abstracta y no se pueden crear instancias de ella. Implementa los servicios que son comunes a todos los tipos de paneles con pestañas.

Actualmente, la biblioteca incluye dos clases derivadas de paneles con pestañas: [clase CTabbedPane](../../mfc/reference/ctabbedpane-class.md) y [clase cmfcoutlookbar (](../../mfc/reference/cmfcoutlookbar-class.md).

Un objeto `CBaseTabbedPane` contiene un puntero a un objeto de la [clase CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) . A continuación, la [clase CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) se convierte en una ventana secundaria del panel con pestañas.

Para obtener más información sobre cómo crear paneles con pestañas, vea clase [CDockablePane](../../mfc/reference/cdockablepane-class.md), clase [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)y [clase cmfcoutlookbar (](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[A cbasepane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxBaseTabbedPane. h

##  <a name="addtab"></a>CBaseTabbedPane:: AddTab

Agrega una nueva pestaña a un panel con pestañas.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parámetros

*pNewBar*<br/>
[in, out] Puntero al panel que se va a agregar. Este puntero puede dejar de ser válido después de llamar a este método. Para obtener más información, vea la sección Comentarios.

*bVisible*<br/>
de TRUE para hacer que la pestaña sea visible; en caso contrario, FALSE.

*bSetActive*<br/>
de TRUE para hacer que la pestaña sea la pestaña activa; en caso contrario, FALSE.

*bDetachable*<br/>
de TRUE para hacer que la pestaña sea desasociable; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se ha agregado correctamente como una pestaña y no se ha destruido en el proceso. FALSE si el panel que se agrega es un objeto de tipo `CBaseTabbedPane`. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Llame a este método para agregar un panel como una nueva pestaña en un panel con pestañas. Si *pNewBar* apunta a un objeto de tipo `CBaseTabbedPane`, todas sus pestañas se copian en el panel con pestañas y, a continuación, se destruye *pNewBar* . Por lo tanto, *pNewBar* se convierte en un puntero no válido y no debe usarse.

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane:: AllowDestroyEmptyTabbedPane

Especifica si se puede destruir un panel con pestañas vacío.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se puede destruir un panel con pestañas vacío; en caso contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Si no se permite la destrucción de un panel con pestañas vacío, el marco de trabajo lo oculta en su lugar.

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane:: ApplyRestoredTabInfo

Carga la configuración de las pestañas del registro y las aplica a un panel con pestañas.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parámetros

*bUseTabIndexes*<br/>
de Este parámetro lo usa internamente el marco de trabajo.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando recarga información de estado de acoplamiento del registro. El método obtiene información sobre el orden de tabulación y los nombres de las pestañas de un panel con pestañas.

##  <a name="canfloat"></a>CBaseTabbedPane:: CanFloat

Especifica si el panel con pestañas puede flotar.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel puede flotar; en caso contrario, FALSE.

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane:: CanSetCaptionTextToTabName

Determina si el título del panel con pestañas debe mostrar el mismo texto que la pestaña activa.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el texto del título del panel con pestañas se establece en el texto de la pestaña activa; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

El método se usa para determinar si el texto que se muestra en el título del panel con pestañas duplica la etiqueta de la pestaña activa. Puede habilitar o deshabilitar esta funcionalidad mediante una llamada a [CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane:: ConvertToTabbedDocument

Convierte uno o más paneles acoplables en documentos con pestañas MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bActiveTabOnly*<br/>
de Al convertir un panel con pestañas, especifique TRUE para convertir solo la pestaña activa. especifique FALSE para convertir todas las pestañas del panel.

##  <a name="detachpane"></a>CBaseTabbedPane::D etachPane

Desasocia un panel del panel con pestañas.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Puntero al panel que se va a desasociar.

*bHide*<br/>
de Parámetro booleano que especifica si el marco oculta el panel una vez desasociado.

### <a name="return-value"></a>Valor devuelto

TRUE si el marco de trabajo desasocia correctamente el panel; FALSE si *pBar* es null o hace referencia a un panel que no está en el panel con pestañas.

### <a name="remarks"></a>Observaciones

El marco de trabajo flota el panel desasociado si es posible. Para obtener más información, vea [a cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane:: EnableSetCaptionTextToTabName

Habilita o deshabilita la capacidad del panel con pestañas para sincronizar el texto del título con el texto de la etiqueta en la pestaña activa.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para sincronizar el título del panel con pestañas con el título de la pestaña activa; en caso contrario, FALSE.

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane:: FillDefaultTabsOrderArray

Restaura el orden de tabulación interno a un estado predeterminado.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Observaciones

Se llama a este método cuando el marco restaura una barra de Outlook a un estado inicial.

##  <a name="findpanebyid"></a>CBaseTabbedPane:: FindPaneByID

Devuelve un panel identificado por el identificador del panel.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parámetros

*uBarID*<br/>
de Especifica el identificador del panel que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un puntero al panel si se encontró; de lo contrario, es NULL.

### <a name="remarks"></a>Observaciones

Este método compara todas las pestañas del panel y devuelve la con el identificador especificado por el parámetro *uBarID* .

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane:: FindBarByTabNumber

Devuelve un panel que reside en una pestaña.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parámetros

*nTabNum*<br/>
de Especifica el índice de base cero de la pestaña que se va a recuperar.

*bGetWrappedBar*<br/>
de TRUE para devolver la ventana subyacente (ajustada) del panel en lugar del propio panel; en caso contrario, FALSE. Esto solo se aplica a los paneles que se derivan de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Valor devuelto

Si se encuentra el panel, se devuelve un puntero válido al panel que se está buscando; de lo contrario, es NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el panel que reside en la pestaña especificada por el parámetro *nTabNum* .

##  <a name="floattab"></a>CBaseTabbedPane:: FloatTab

Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in, out] Puntero al panel que se va a flotar.

*nTabID*<br/>
de Especifica el índice de base cero de la pestaña que se va a flotar.

*dockMethod*<br/>
de Especifica el método que se va a usar para hacer que el panel sea flotante. Para obtener más información, vea la sección Comentarios.

*bHide*<br/>
de TRUE para ocultar el panel antes de flotar; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel está flotando; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para flotar un panel que actualmente reside en una pestaña desasociable.

Si desea desasociar un panel mediante programación, especifique DM_SHOW para el parámetro *dockMethod* . Si desea flotar el panel en la misma posición en la que se flota previamente, especifique DM_DBL_CLICK como el parámetro *dockMethod* .

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane:: GetDefaultTabsOrder

Devuelve el orden predeterminado de las fichas en el panel.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CArray` que especifica el orden predeterminado de las fichas en el panel.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando una barra de Outlook se restablece a un estado inicial.

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane:: GetFirstVisibleTab

Recupera un puntero a la primera pestaña mostrada.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
de Referencia a un entero. Este método escribe el índice de base cero de la primera pestaña mostrada en este parámetro o-1 si no se encuentra ninguna pestaña mostrada.

### <a name="return-value"></a>Valor devuelto

Si es correcto, un puntero a la primera pestaña mostrada; de lo contrario, es NULL.

##  <a name="getminsize"></a>CBaseTabbedPane:: GetMinSize

Recupera el tamaño mínimo permitido para el panel.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parámetros

*size*<br/>
enuncia `CSize` objeto que se rellena con el tamaño mínimo permitido.

### <a name="remarks"></a>Observaciones

Si el control coherente del tamaño mínimo del panel está activo ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize) *), el tamaño se* rellena con el tamaño mínimo permitido para la pestaña activa. de lo contrario, el *tamaño* se rellena con el valor devuelto de [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>CBaseTabbedPane:: GetPaneIcon

Recupera el tamaño mínimo permitido para el panel.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parámetros

*size*<br/>
enuncia `CSize` objeto que se rellena con el tamaño mínimo permitido.

### <a name="remarks"></a>Observaciones

Si el control coherente del tamaño mínimo del panel está activo ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize) *), el tamaño se* rellena con el tamaño mínimo permitido para la pestaña activa. de lo contrario, el *tamaño* se rellena con el valor devuelto de [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>CBaseTabbedPane:: GetPaneList

Devuelve una lista de paneles contenidos en el panel con pestañas.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parámetros

*LST*<br/>
enuncia `CObList` que se rellena con los paneles contenidos en el panel con pestañas.

*pRTCFilter*<br/>
de Si no es NULL, la lista devuelta contiene solo los paneles que son de la clase en tiempo de ejecución especificada.

##  <a name="gettabarea"></a>CBaseTabbedPane:: GetTabArea

Devuelve los rectángulos delimitadores para las áreas de la pestaña superior e inferior.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
enuncia Recibe las coordenadas de pantalla del área superior de la pestaña.

*rectTabAreaBottom*<br/>
enuncia Recibe las coordenadas de pantalla del área de la pestaña inferior.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar los rectángulos delimitadores, en coordenadas de pantalla, para las áreas de la pestaña superior e inferior.

##  <a name="gettabsnum"></a>CBaseTabbedPane:: GetTabsNum

Devuelve el recuento de pestañas de una ventana de pestaña.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Valor devuelto

El número de pestañas en el panel con pestañas.

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane:: GetUnderlyingWindow

Obtiene la ventana de pestaña subyacente (ajustada).

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de ficha subyacente.

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane:: GetVisibleTabsNum

Devuelve el recuento de pestañas visibles.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Valor devuelto

El número de pestañas visibles, que serán mayores o iguales que cero.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar el número de pestañas visibles en el panel con pestañas.

##  <a name="hasautohidemode"></a>CBaseTabbedPane:: HasAutoHideMode

Determina si el panel con pestañas se puede cambiar a modo de ocultación automática.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se puede cambiar al modo de ocultar automáticamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el modo Ocultar automáticamente está deshabilitado, no se muestra ningún botón anclar en el título del panel con pestañas.

##  <a name="ishidesingletab"></a>CBaseTabbedPane:: IsHideSingleTab

Determina si el panel con pestañas está oculto si solo se muestra una pestaña.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana de tabulación no se muestra cuando solo hay una pestaña visible; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el panel no se muestra porque solo hay una pestaña abierta, puede llamar a este método para determinar si el panel con pestañas funciona correctamente.

##  <a name="removepane"></a>CBaseTabbedPane:: RemovePane

Quita un panel del panel con pestañas.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in, out] Puntero al panel que se va a quitar del panel con pestañas.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se quitó correctamente del panel con pestañas y si el panel con pestañas sigue siendo válido. FALSE si se ha quitado el último panel del panel con pestañas y el panel con pestañas está a punto de ser destruido. Si el valor devuelto es FALSE, no utilice el panel con pestañas más.

### <a name="remarks"></a>Observaciones

Llame a este método para quitar el panel especificado por el parámetro *pBar* del panel con pestañas.

##  <a name="setautodestroy"></a>CBaseTabbedPane:: SetAutoDestroy

Determina si la barra de control con pestañas se destruirá automáticamente.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
de TRUE si el panel con pestañas se creó dinámicamente y no está controlando su duración; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Establezca el modo de destrucción automática en TRUE si crea un panel con pestañas dinámicamente y si no controla su duración. Si el modo de destrucción automática es TRUE, el marco de trabajo destruirá automáticamente el panel con pestañas.

##  <a name="showtab"></a>CBaseTabbedPane:: ShowTab

Muestra u oculta una pestaña.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Puntero al panel que se va a mostrar u ocultar.

*bShow*<br/>
de TRUE para mostrar el panel; FALSE para ocultar el panel.

*bDelay*<br/>
de TRUE para retrasar el ajuste del diseño de pestañas; en caso contrario, FALSE.

*bActivate*<br/>
de TRUE para hacer que la pestaña sea la pestaña activa; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si la pestaña se mostró u ocultó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando se llama a este método, se muestra u oculta un panel, dependiendo del valor del parámetro *bShow* . Si oculta una pestaña y es la última pestaña visible de la ventana de pestaña subyacente, se oculta el panel con pestañas. Si muestra una pestaña cuando anteriormente no había ninguna pestaña visible, se muestra el panel con pestañas.

##  <a name="recalclayout"></a>CBaseTabbedPane:: RecalcLayout

Vuelve a calcular la información de diseño del panel.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Observaciones

Si el panel es flotante, este método notifica al marco de trabajo que cambie el tamaño del panel al tamaño actual del marco reducido.

Si el panel está acoplado, este método no hace nada.

##  <a name="setautohidemode"></a>CBaseTabbedPane:: SetAutoHideMode

Establece el modo de ocultación automática para los paneles desasociables en el panel con pestañas.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMode*<br/>
de TRUE para habilitar el modo de ocultación automática; FALSE para habilitar el modo de acoplamiento normal.

*dwAlignment*<br/>
de Especifica la alineación del panel de ocultación automática que se va a crear. Para obtener una lista de los valores posibles, vea [CPane:: MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[in, out] Puntero a la barra de herramientas de ocultación automática actual. Puede ser NULL.

*bUseTimer*<br/>
de Especifica si se va a usar el efecto de ocultación automática cuando el usuario cambia el panel al modo de ocultación automática o a ocultar el panel inmediatamente.

### <a name="return-value"></a>Valor devuelto

Puntero a la barra de herramientas de ocultación automática que se crea al cambiar al modo de ocultación automática o NULL si no se crea ninguna barra de herramientas.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando un usuario elige el botón anclar para cambiar el panel con pestañas al modo de ocultación automática o al modo de acoplamiento normal.

El modo de ocultación automática se establece para cada panel desasociable en el panel con pestañas. Los paneles que no se pueden desasociar se omiten. Para obtener más información, vea [CMFCBaseTabCtrl:: EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Llame a este método para cambiar mediante programación un panel con pestañas al modo de ocultación automática. El panel debe estar acoplado a la ventana de marco principal ( [CDockablePane:: GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) debe devolver un puntero válido a [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
