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
ms.openlocfilehash: ce7c48263ed511545757c94d61552e6206e74a00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352853"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane (clase)

Extiende la funcionalidad de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) para permitir la creación de ventanas con pestañas.

## <a name="syntax"></a>Sintaxis

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Agrega una nueva pestaña a un panel con pestañas.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con pestañas vacío.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Aplica la configuración de pestañas, que se cargan desde el registro, a un panel con fichas.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Determina si el panel puede flotar. (Reemplaza [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título del panel con fichas debe mostrar el mismo texto que la pestaña activa.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Reemplaza [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Convierte uno o más paneles acoplables en documentos con fichas MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Habilita o deshabilita la capacidad del panel con pestañas para sincronizar el texto del título con el texto de la etiqueta en la pestaña activa.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaura el orden de tabulación interno a un estado predeterminado.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Devuelve un panel que reside en una pestaña cuando la pestaña se identifica mediante un índice de ficha de base cero.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Devuelve un panel identificado por el identificador del panel.|
|[CBaseTabbedPane::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Devuelve el orden predeterminado de las pestañas en el panel.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Recupera un puntero a la primera pestaña mostrada.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Recupera el tamaño mínimo permitido para el panel. (Reemplaza [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Devuelve un identificador al icono del panel. (Reemplaza [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Devuelve una lista de paneles que se encuentran en el panel con fichas.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Devuelve los rectángulos delimitadores de las áreas de pestaña superior e inferior.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Devuelve el recuento de pestañas en una ventana de pestañas.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtiene la ventana de ficha subyacente (envuelta).|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Devuelve el recuento de pestañas mostradas.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Determina si el panel con pestañas se puede cambiar al modo de ocultación automática.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Determina si el panel con fichas está oculto si solo se muestra una pestaña.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Se utiliza internamente durante la serialización.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Vuelve a calcular la información de diseño del panel. (Reemplaza [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Quita un panel del panel con pestañas.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Se utiliza internamente durante la serialización.|
|`CBaseTabbedPane::Serialize`|(Reemplaza [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Se utiliza internamente durante la serialización.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Determina si la barra de control con pestañas se destruirá automáticamente.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Alterna el panel de acoplamiento entre el modo mostrado y el modo de ocultación automática. (Reemplaza [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::ShowTab](#showtab)|Muestra u oculta una pestaña.|

## <a name="remarks"></a>Observaciones

Esta clase es una clase abstracta y no se pueden crear instancias. Implementa los servicios que son comunes a todos los tipos de paneles con pestañas.

Actualmente, la biblioteca incluye dos clases de panel con pestañas derivadas: [CTabbedPane (Clase)](../../mfc/reference/ctabbedpane-class.md) y [CMFCOutlookBar (Clase).](../../mfc/reference/cmfcoutlookbar-class.md)

Un `CBaseTabbedPane` objeto ajusta un puntero a un [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md) objeto. [CMFCBaseTabCtrl clase,](../../mfc/reference/cmfcbasetabctrl-class.md) a continuación, se convierte en una ventana secundaria del panel con fichas.

Para obtener más información acerca de cómo crear paneles con fichas, vea [CDockablePane (Clase)](../../mfc/reference/cdockablepane-class.md), [CTabbedPane (Clase)](../../mfc/reference/ctabbedpane-class.md)y [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::AddTab

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
[adentro, fuera] Puntero al panel que se va a agregar. Este puntero puede volverse inválido después de llamar a este método. Para obtener más información, vea la sección Comentarios.

*bVisible*<br/>
[en] TRUE para que la pestaña sea visible; de lo contrario, FALSE.

*bSetActive*<br/>
[en] TRUE para que la pestaña sea la pestaña activa; de lo contrario, FALSE.

*bDesmontable*<br/>
[en] TRUE para que la pestaña se pueda separar; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel se agregó correctamente como una pestaña y no se destruyó en el proceso. FALSE si el panel que se `CBaseTabbedPane`va a agregar es un objeto de tipo . Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Llame a este método para agregar un panel como una nueva pestaña en un panel con fichas. Si *pNewBar* apunta a `CBaseTabbedPane`un objeto de tipo , todas sus fichas se copian en el panel con fichas y, a continuación, *pNewBar* se destruye. Por lo tanto, *pNewBar* se convierte en un puntero no válido y no se debe usar.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Especifica si se puede destruir un panel con pestañas vacío.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se puede destruir un panel con pestañas vacío; de lo contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Si no se permite destruir un panel con pestañas vacío, el marco de trabajo oculta el panel en su lugar.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Carga la configuración de pestañas del registro y la aplica a un panel con fichas.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parámetros

*bUseTabIndexes*<br/>
[en] El marco de trabajo utiliza este parámetro internamente.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando vuelve a cargar la información de estado de acoplamiento del registro. El método obtiene información sobre el orden de tabulación y los nombres de tabulación de un panel con fichas.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat

Especifica si el panel con fichas puede flotar.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el panel puede flotar; de lo contrario, FALSE.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Determina si el título del panel con fichas debe mostrar el mismo texto que la pestaña activa.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el texto de título del panel con fichas se establece en el texto de la pestaña activa; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El método se utiliza para determinar si el texto que se muestra en el título del panel con pestañas duplica la etiqueta de la pestaña activa. Puede habilitar o deshabilitar esta funcionalidad llamando a [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Convierte uno o más paneles acoplables en documentos con fichas MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bActiveTabOnly*<br/>
[en] Al convertir un panel con fichas, especifique TRUE para convertir solo la pestaña activa. Especificar FALSE para convertir todas las fichas del panel.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane

Separa un panel del panel con fichas.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[en] Puntero al panel para separar.

*bOcultar*<br/>
[en] Parámetro booleano que especifica si el marco de trabajo oculta el panel después de separarlo.

### <a name="return-value"></a>Valor devuelto

TRUESi el marco de trabajo separa correctamente el panel; FALSE si *pBar* es NULL o hace referencia a un panel que no está en el panel con fichas.

### <a name="remarks"></a>Observaciones

El marco de trabajo flota el panel separado si es posible. Para obtener más información, vea [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Habilita o deshabilita la capacidad del panel con pestañas para sincronizar el texto del título con el texto de la etiqueta en la pestaña activa.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para sincronizar el título del panel con pestañas con el título de tabulación activo; de lo contrario, FALSE.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Restaura el orden de tabulación interno a un estado predeterminado.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Observaciones

Se llama a este método cuando el marco de trabajo restaura una barra de Outlook a un estado inicial.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Devuelve un panel identificado por el identificador del panel.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parámetros

*uBarID*<br/>
[en] Especifica el identificador del panel que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un puntero al panel si se encontró; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este método compara todas las pestañas del panel y devuelve la que tiene el identificador especificado por el parámetro *uBarID.*

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Devuelve un panel que reside en una pestaña.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parámetros

*nTabNum*<br/>
[en] Especifica el índice de base cero de la ficha que se va a recuperar.

*bGetWrappedBar*<br/>
[en] TRUE para devolver la ventana subyacente (envuelta) del panel en lugar del propio panel; de lo contrario FALSO. Esto solo se aplica a los paneles derivados de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Valor devuelto

Si se encuentra el panel, se devuelve un puntero válido al panel que se busca; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el panel que reside en la pestaña especificada por el *nTabNum* parámetro.

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab

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
[adentro, fuera] Puntero al panel para flotar.

*nTabID*<br/>
[en] Especifica el índice de base cero de la ficha para flotante.

*dockMethod*<br/>
[en] Especifica el método que se usará para que el panel sea flotante. Para obtener más información, vea la sección Comentarios.

*bOcultar*<br/>
[en] TRUE para ocultar el panel antes de flotar; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel flotaba; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para flotar un panel que reside actualmente en una pestaña desmontable.

Si desea separar un panel mediante programación, especifique DM_SHOW para el *dockMethod* parámetro. Si desea flotar el panel en la misma posición en la que flotaba anteriormente, especifique DM_DBL_CLICK como el parámetro *dockMethod.*

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Devuelve el orden predeterminado de las pestañas en el panel.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CArray` que especifica el orden predeterminado de las fichas en el panel.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando una barra de Outlook se restablece a un estado inicial.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Recupera un puntero a la primera pestaña mostrada.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
[en] Una referencia a un entero. Este método escribe el índice de base cero de la primera pestaña mostrada en este parámetro, o -1 si no se encuentra ninguna pestaña mostrada.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un puntero a la primera pestaña mostrada; de lo contrario, NULL.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Recupera el tamaño mínimo permitido para el panel.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
[fuera] Objeto `CSize` que se rellena con el tamaño mínimo permitido.

### <a name="remarks"></a>Observaciones

Si el control coherente de los tamaños mínimos del panel está activo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), el *tamaño* se rellena con el tamaño mínimo permitido para la pestaña activa. De lo contrario, *el tamaño* se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Recupera el tamaño mínimo permitido para el panel.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
[fuera] Objeto `CSize` que se rellena con el tamaño mínimo permitido.

### <a name="remarks"></a>Observaciones

Si el control coherente de los tamaños mínimos del panel está activo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), el *tamaño* se rellena con el tamaño mínimo permitido para la pestaña activa. De lo contrario, *el tamaño* se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::GetPaneList

Devuelve una lista de paneles que se encuentran en el panel con fichas.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
[fuera] A `CObList` que se rellena con los paneles que se encuentran en el panel con fichas.

*pRTCFilter*<br/>
[en] Si no es NULL, la lista devuelta contiene solo los paneles que son de la clase de tiempo de ejecución especificada.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Devuelve los rectángulos delimitadores de las áreas de pestaña superior e inferior.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
[fuera] Recibe las coordenadas de pantalla del área de la pestaña superior.

*rectTabAreaBottom*<br/>
[fuera] Recibe las coordenadas de pantalla del área de la pestaña inferior.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar los rectángulos delimitadores, en coordenadas de pantalla, para las áreas de tabulación superior e inferior.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Devuelve el recuento de pestañas en una ventana de pestañas.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Valor devuelto

El número de pestañas en el panel con fichas.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Obtiene la ventana de ficha subyacente (envuelta).

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de ficha subyacente.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Devuelve el recuento de pestañas visibles.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Valor devuelto

El número de pestañas visibles, que será mayor o igual que cero.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar el número de fichas visibles en el panel con fichas.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Determina si el panel con pestañas se puede cambiar a modo de ocultación automática.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el panel se puede cambiar al modo de ocultación automática; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el modo de ocultación automática está deshabilitado, no se muestra ningún botón de pasador en el título del panel con pestañas.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Determina si el panel con fichas está oculto si solo se muestra una pestaña.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana de tabulación no se muestra cuando solo hay una pestaña visible; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el panel no se muestra porque solo una pestaña está abierta, puede llamar a este método para determinar si el panel con fichas funciona correctamente.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::RemovePane

Quita un panel del panel con pestañas.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[adentro, fuera] Puntero al panel que se va a quitar del panel con fichas.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel se quitó correctamente del panel con fichas y si el panel con fichas sigue siendo válido. FALSE si el último panel se ha quitado del panel con fichas y el panel con fichas está a punto de destruirse. Si el valor devuelto es FALSE, ya no use el panel con fichas.

### <a name="remarks"></a>Observaciones

Llame a este método para quitar el panel especificado por el *pBar* parámetro desde el panel con fichas.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Determina si la barra de control con pestañas se destruirá automáticamente.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
[en] TRUESi el panel con pestañas se creó dinámicamente y no controla su duración; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Establezca el modo de destrucción automática en TRUE si crea un panel con pestañas dinámicamente y si no controla su duración. Si el modo de destrucción automática es TRUE, el marco de trabajo destruirá automáticamente el panel con pestañas.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::ShowTab

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
[en] Puntero al panel para mostrar u ocultar.

*bMostrar*<br/>
[en] TRUE para mostrar el panel; FALSE para ocultar el panel.

*bDelay*<br/>
[en] TRUE para retrasar el ajuste del diseño de ficha; de lo contrario, FALSE.

*bActivar*<br/>
[en] TRUE para que la pestaña sea la pestaña activa; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUESi la pestaña se mostró u ocultó correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando se llama a este método, se muestra u oculta un panel, en función del valor del parámetro *bShow.* Si oculta una pestaña y es la última pestaña visible en la ventana de ficha subyacente, el panel con fichas se oculta. Si muestra una pestaña cuando anteriormente no había pestañas visibles, se muestra el panel con pestañas.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Vuelve a calcular la información de diseño del panel.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Observaciones

Si el panel está flotante, este método notifica al marco de trabajo que cambie el tamaño del panel al tamaño actual del minifotograma.

Si el panel está acoplado, este método no hace nada.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Establece el modo de ocultación automática para los paneles desmontables en el panel con fichas.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMode*<br/>
[en] TRUE para habilitar el modo de ocultación automática; FALSE para habilitar el modo de acoplamiento normal.

*dwAlignment*<br/>
[en] Especifica la alineación del panel de ocultación automática que se va a crear. Para obtener una lista de valores posibles, vea [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[adentro, fuera] Un puntero a la barra de herramientas de ocultación automática actual. Puede ser NULL.

*bUseTimer*<br/>
[en] Especifica si se debe utilizar el efecto de ocultación automática cuando el usuario cambia el panel al modo de ocultación automática o para ocultar el panel inmediatamente.

### <a name="return-value"></a>Valor devuelto

Un puntero a la barra de herramientas de ocultación automática que se crea al cambiar al modo de ocultación automática, o NULL si no se crea ninguna barra de herramientas.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando un usuario elige el botón de anclar para cambiar el panel con fichas al modo de ocultación automática o al modo de acoplamiento normal.

El modo de ocultación automática se establece para cada panel desmontable en el panel con fichas. Los paneles que no son desmontables se omiten. Para obtener más información, vea [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Llame a este método para cambiar un panel con fichas al modo de ocultación automática mediante programación. El panel debe acoplarse a la ventana de marco principal ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) debe devolver un puntero válido a [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
