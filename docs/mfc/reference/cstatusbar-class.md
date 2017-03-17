---
title: CStatusBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- indicators, status bar
- CStatusBar class
- status bars
- indicators
- status indicators
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e96070041ef5bcee0865991a14b6484082d8fc91
ms.lasthandoff: 02/24/2017

---
# <a name="cstatusbar-class"></a>CStatusBar (clase)
Una barra de control con una fila de paneles de salida de texto o "indicadores".  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|Construye un objeto `CStatusBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtiene el índice para un identificador determinado indicador.|  
|[CStatusBar::Create](#create)|Crea la barra de estado, que se conecta a la `CStatusBar` de objetos y establece el alto de fuente y barra inicial.|  
|[CStatusBar:: CreateEx](#createex)|Crea un `CStatusBar` objeto estilos adicionales para el objeto incrustado `CStatusBarCtrl` objeto.|  
|[CStatusBar::DrawItem](#drawitem)|Se llama cuando la apariencia de una barra de estado dibujados por el propietario cambia control.|  
|[CStatusBar::GetItemID](#getitemid)|Obtiene el identificador de indicador de un índice determinado.|  
|[CStatusBar::GetItemRect](#getitemrect)|Obtiene Mostrar rectángulo para un índice determinado.|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtiene el Id. de indicador, el estilo y el ancho de un índice determinado.|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtiene el estilo del indicador de un índice determinado.|  
|[CStatusBar::GetPaneText](#getpanetext)|Obtiene el texto de indicador para un índice determinado.|  
|[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)|Permite el acceso directo al control subyacente común.|  
|[CStatusBar:: SetIndicators](#setindicators)|Establece el Id. de indicador.|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Establece el identificador de indicadores, estilo y ancho de un índice determinado.|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del indicador de un índice determinado.|  
|[CStatusBar::SetPaneText](#setpanetext)|Establece el texto de indicador de un índice determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Los paneles de salida se utilizan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos son las líneas de mensaje de Ayuda de menú que se describe brevemente el comando de menú seleccionado y los indicadores que muestran el estado de Bloq Despl, BLOQ NUM y otras claves.  
  
 [CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl), una función miembro nueva para MFC 4.0, permite aprovechar la compatibilidad del control común de Windows para la personalización y funcionalidad adicional de la barra de estado. `CStatusBar`las funciones de miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetStatusBarCtrl`, puede dar a las barras de estado aún más las características de una barra de estado de Windows 95 ó 98. Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un `CStatusBarCtrl` objeto. Consulte [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas con controles comunes de Windows. Para obtener información general sobre los controles comunes, consulte [controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El marco de trabajo almacena información de indicador en una matriz con el indicador situado en la posición 0. Cuando se crea una barra de estado, use una matriz de identificadores que el marco de trabajo se asocia a los indicadores correspondientes de cadena. A continuación, puede utilizar un identificador de cadena o un índice para tener acceso a un indicador.  
  
 De forma predeterminada, el primer indicador es "flexible": ocupa la longitud de la barra de estado no utilizada por los paneles de indicador, para que los otros paneles están alineados a la derecha.  
  
 Para crear una barra de estado, siga estos pasos:  
  
1.  Construir la `CStatusBar` objeto.  
  
2.  Llame a la [crear](#create) (o [CreateEx](#createex)) (función) para crear la ventana de la barra de estado y adjuntarlo a la `CStatusBar` objeto.  
  
3.  Llame a [SetIndicators](#setindicators) para asociar un identificador de cadena de cada indicador.  
  
 Hay tres maneras de actualizar el texto de un panel de barra de estado:  
  
1.  Llame a [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) para actualizar el texto en el panel 0.  
  
2.  Llame a [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) en la barra de estado `ON_UPDATE_COMMAND_UI` controlador.  
  
3.  Llame a [denominada SetPaneText](#setpanetext) para actualizar el texto para cualquier panel.  
  
 Llame a [SetPaneStyle](#setpanestyle) para actualizar el estilo de un panel de barra de estado.  
  
 Para obtener más información sobre el uso de `CStatusBar`, vea el artículo [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [Nota técnica 31: barras de Control](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 Obtiene el índice de indicador para un identificador dado.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDFind`  
 Identificador de cadena del indicador cuyo índice es va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del indicador de si es correcto; -1 si no funciona correctamente.  
  
### <a name="remarks"></a>Comentarios  
 El índice del primer indicador es 0.  
  
##  <a name="create"></a>CStatusBar::Create  
 Crea un estado de la barra (una ventana secundaria) y lo asocia a la `CStatusBar` objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto cuya ventana de Windows es el elemento primario de la barra de estado.  
  
 `dwStyle`  
 El estilo de barra de estado. Además de las ventanas estándares [estilos](../../mfc/reference/window-styles.md), se admiten estos estilos.  
  
- `CBRS_TOP`Barra de control está en la parte superior de la ventana de marco.  
  
- `CBRS_BOTTOM`Barra de control está en la parte inferior de la ventana de marco.  
  
- `CBRS_NOALIGN`Barra de control no se cambia de posición cuando se cambia el elemento primario.  
  
 `nID`  
 Identificador de ventana secundaria. de la barra de herramientas  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 También establece la fuente inicial y el estado de alto de la barra en un valor predeterminado.  
  
##  <a name="createex"></a>CStatusBar:: CreateEx  
 Llame a esta función para crear un estado de la barra (una ventana secundaria) y asociarla con el `CStatusBar` objeto.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto cuya ventana de Windows es el elemento primario de la barra de estado.  
  
 `dwCtrlStyle`  
 Estilos adicionales para la creación de los datos incrustados [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objeto. El valor predeterminado especifica una barra de estado sin un control de tamaño o la información sobre herramientas admitir. Estilos de barra de estado compatibles son:  
  
- **SBARS_SIZEGRIP** el control de barra de estado incluye un control de tamaño en el extremo derecho de la barra de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular en la que el usuario hacer clic y arrastre para cambiar el tamaño de la ventana primaria.  
  
- **SBT_TOOLTIPS** la barra de estado es compatible con la información sobre herramientas.  
  
 Para obtener más información acerca de estos estilos, consulte [configuración de CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).  
  
 `dwStyle`  
 El estilo de barra de estado. El valor predeterminado especifica que se ha creado una barra de estado visible en la parte inferior de la ventana de marco. Aplicar cualquier combinación de estilos de control que aparece en la barra de estado [estilos de ventana](../../mfc/reference/window-styles.md) y [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Sin embargo, este parámetro siempre debe incluir los estilos WS_CHILD y WS_VISIBLE.  
  
 `nID`  
 Identificador de ventana secundaria de la barra de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función también se establece la fuente inicial y establece el estado alto de la barra en un valor predeterminado.  
  
 Utilice `CreateEx`, en lugar de [crear](#create), cuando determinados estilos deben estar presentes durante la creación del control de barra de estado incrustada. Por ejemplo, establecer `dwCtrlStyle` a **SBT_TOOLTIPS** para mostrar información sobre herramientas en un objeto de la barra de estado.  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 Construye un `CStatusBar` objeto, crea una fuente de la barra de estado de forma predeterminada si es necesario y establece las características de fuente a los valores predeterminados.  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 El marco de trabajo cuando la apariencia de una barra de estado dibujada cambia llama a esta función miembro.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CStatusBar` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de la finalización de esta función miembro.  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 Devuelve el identificador del indicador especificado por `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del indicador cuyo identificador es va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del indicador especificado por `nIndex`.  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 Copia las coordenadas del indicador especificado por `nIndex` en la estructura que señala `lpRect`.  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del indicador cuyas coordenadas de rectángulo son va a recuperar.  
  
 `lpRect`  
 Apunta a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que recibirá las coordenadas del indicador especificado por `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 Las coordenadas están en píxeles con respecto a la esquina superior izquierda de la barra de estado.  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 Conjuntos de `nID`, `nStyle`, y `cxWidth` para el Id., el estilo y el ancho del panel indicador en la ubicación especificada por `nIndex`.  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del panel cuya información va a recuperar.  
  
 `nID`  
 Hacer referencia a un **UINT** que se establece en el identificador del panel.  
  
 `nStyle`  
 Hacer referencia a un **UINT** que se establece el estilo del panel.  
  
 `cxWidth`  
 Referencia a un entero que se establece el ancho del panel.  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 Llame a esta función miembro para recuperar el estilo del panel de la barra de estado.  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de la sección cuyo estilo sea va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo del panel de barra de estado especificado por `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 Estilo de un panel determina cómo aparece el panel.  
  
 Para obtener una lista de estilos disponibles para las barras de estado, consulte [crear](#create).  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 Llame a esta función miembro para recuperar el texto que aparece en un panel de barra de estado.  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  ```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be retrieved.  
  
 `rString`  
 A reference to a [CString](../../atl-mfc-shared/reference/cstringt-class.md) object that contains the text to be retrieved.  
  
### Return Value  
 A `CString` object containing the pane's text.  
  
### Remarks  
 The second form of this member function fills a `CString` object with the string text.  
  
##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl  
 This member function allows direct access to the underlying common control.  
  
```  
GetStatusBarCtrl() de aspecto de CStatusBarCtrl const;  
```  
  
### Return Value  
 Contains a reference to a [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) object.  
  
### Remarks  
 Use `GetStatusBarCtrl` to take advantage of the functionality of the Windows status-bar common control, and to take advantage of the support [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) provides for status-bar customization. For example, by using the common control, you can specify a style that includes a sizing grip on the status bar, or you can specify a style to have the status bar appear at the top of the parent window's client area.  
  
 For more general information about common controls, See [Common Controls](http://msdn.microsoft.com/library/windows/desktop/bb775493) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setindicators"></a>  CStatusBar::SetIndicators  
 Sets each indicator's ID to the value specified by the corresponding element of the array `lpIDArray`, loads the string resource specified by each ID, and sets the indicator's text to the string.  
  
```  
BOOL SetIndicators (const UINT * lpIDArray,  
    int nIDCount);
```  
  
### Parameters  
 `lpIDArray`  
 Pointer to an array of IDs.  
  
 `nIDCount`  
 Number of elements in the array pointed to by `lpIDArray`.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo  
 Sets the specified indicator pane to a new ID, style, and width.  
  
```  
void SetPaneInfo (int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### Parameters  
 `nIndex`  
 Index of the indicator pane whose style is to be set.  
  
 `nID`  
 New ID for the indicator pane.  
  
 `nStyle`  
 New style for the indicator pane.  
  
 `cxWidth`  
 New width for the indicator pane.  
  
### Remarks  
 The following indicator styles are supported:  
  
- **SBPS_NOBORDERS** No 3-D border around the pane.  
  
- **SBPS_POPOUT** Reverse border so that text "pops out."  
  
- **SBPS_DISABLED** Do not draw text.  
  
- **SBPS_STRETCH** Stretch pane to fill unused space. Only one pane per status bar can have this style.  
  
- **SBPS_NORMAL** No stretch, borders, or pop-out.  
  
##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle  
 Call this member function to set the style of a status bar's pane.  
  
```  
void SetPaneStyle (int nIndex,  
    UINT nStyle);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose style is to be set.  
  
 `nStyle`  
 Style of the pane whose style is to be set.  
  
### Remarks  
 A pane's style determines how the pane appears.  
  
 For a list of styles available for status bars, see [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>  CStatusBar::SetPaneText  
 Call this member function to set the pane text to the string pointed to by `lpszNewText`.  
  
```  
BOOL denominada SetPaneText (int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bactualización = TRUE);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be set.  
  
 `lpszNewText`  
 Pointer to the new pane text.  
  
 *bUpdate*  
 If **TRUE**, the pane is invalidated after the text is set.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
### Remarks  
 After you call `SetPaneText`, you must add a UI update handler to display the new text in the status bar.  
  
### Example  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## See Also  
 [MFC Sample CTRLBARS](../../visual-cpp-samples.md)   
 [MFC Sample DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)

