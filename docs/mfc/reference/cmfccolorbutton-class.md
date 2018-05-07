---
title: Clase CMFCColorButton | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cea6fc2a543a528a0838479b2c47bea99f21cf96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfccolorbutton-class"></a>Clase CMFCColorButton
El `CMFCColorButton` y [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) clases se utilizan conjuntamente para implementar un control de selector de color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construye un nuevo objeto `CMFCColorButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" que se coloca encima de los botones de color normal. (El botón automático estándar del sistema tiene la etiqueta **automática**.)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otras" que se coloca debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otros" botón **más colores**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automática actual.|  
|[CMFCColorButton::GetColor](#getcolor)|Recupera el color del botón.|  
|[CMFCColorButton::SetColor](#setcolor)|Establece el color del botón.|  
|[CMFCColorButton::SetColorName](#setcolorname)|Establece un nombre de color.|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas en el cuadro de diálogo de selector de color.|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Especifica una lista de colores específicos del documento que se muestran en el cuadro de diálogo de selector de color.|  
|[CMFCColorButton::SetPalette](#setpalette)|Especifica una paleta de colores de pantalla estándar.|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|Cambia el tamaño del control de botón, según su tamaño de texto e imagen.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indica si el botón de color actual se muestra en el estilo visual de Windows XP.|  
|[CMFCColorButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para mostrar una imagen del botón.|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Lo llama el marco de trabajo para mostrar el borde del botón.|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Lo llama el marco para mostrar un rectángulo de foco cuando el botón tiene un enfoque.|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Lo llama el marco cuando el cuadro de diálogo de selector de color está a punto de mostrarse.|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializa el `m_pPalette` protegido miembro de datos a la paleta especificada o la paleta del sistema de forma predeterminada.|  
|[CMFCColorButton::UpdateColor](#updatecolor)|Lo llama el marco cuando el usuario selecciona un color de la paleta de cuadro de diálogo de selector de color.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|`m_bAltColorDlg`|Un valor booleano. Si `TRUE`, el marco de trabajo muestra el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo de color cuando la *otros* se hace clic en el botón, o si `FALSE`, el cuadro de diálogo de color de sistema. El valor predeterminado es `TRUE`. Para obtener más información, consulte [CMFCColorButton::EnableOtherButton](#enableotherbutton).|  
|`m_bAutoSetFocus`|Un valor booleano. Si `TRUE`, el marco de trabajo establece el foco en el menú de color cuando se muestra el menú, o si `FALSE`, no cambia el foco. El valor predeterminado es `TRUE`.|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indica si está habilitado el modo de personalización para el botón de color.|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor. Contiene el color seleccionado actualmente.|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor. Contiene el color predeterminado seleccionado actualmente.|  
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores. Contiene los colores disponibles actualmente.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores. Contiene los colores del documento actual.|  
|`m_nColumns`|Entero. Contiene el número de columnas que se muestran en la cuadrícula de colores en un menú de selección de color.|  
|`m_pPalette`|Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md). Contiene los colores que están disponibles en el menú de selección de color actual.|  
|`m_pPopup`|Un puntero a un [CMFCColorPopupMenu clase](../../mfc/reference/cmfccolorpopupmenu-class.md) objeto. El menú de selección de color que se muestra al hacer clic en el botón de color.|  
|`m_strAutoColorText`|Una cadena. La etiqueta del botón "automático" en un menú de selección de color.|  
|`m_strDocColorsText`|Una cadena. La etiqueta del botón en un menú de selección de color que se muestra los colores del documento.|  
|`m_strOtherText`|Una cadena. La etiqueta del botón "otro" en un menú de selección de color.|  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, la `CMFCColorButton` clase se comporta como un botón de comando que abre un cuadro de diálogo de selector de color. El cuadro de diálogo de selector de color contiene una matriz de botones de color pequeñas y un "otro" botón que muestra un selector de colores personalizados. (El sistema estándar que tiene la etiqueta "otros" botón **más colores**.) Cuando un usuario selecciona un nuevo color, el `CMFCColorButton` objeto refleje el cambio y muestra el color seleccionado.  
  
 Crear un control de botón de color directamente en el código o mediante el **ClassWizard** herramienta y una plantilla de cuadro de diálogo. Si crea un control de botón de color directamente, agregar un `CMFCColorButton` variable a su aplicación y, después, llame al constructor y `Create` métodos de la `CMFCColorButton` objeto. Si usas el **ClassWizard**, agregue un `CButton` variable a la aplicación y, a continuación, cambie el tipo de la variable de `CButton` a `CMFCColorButton`.  
  
 El cuadro de diálogo de selector de color ( [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md)) se muestra por el [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método cuando el marco llama a la `OnLButtonDown` controlador de eventos. El [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método se puede invalidar para admitir la selección de color personalizado.  
  
 El `CMFCColorButton` objeto notifica a su elemento primario que está cambiando un color al enviarlo una `WM_COMMAND | BN_CLICKED` notificación. El elemento primario usa el [CMFCColorButton::GetColor](#getcolor) método para recuperar el color actual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un botón en color con varios métodos en la `CMFCColorButton` clase. Los métodos de establecer el color del botón de color y su número de columnas y habilitar automático y los demás botones. Este ejemplo forma parte de la [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton  
 Construye un nuevo objeto `CMFCColorButton`.  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton  
 Habilitar o deshabilitar el botón "automático" de un control de selector de color y establecer el color automático (predeterminado).  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica el texto del botón automática.  
  
 [in] `colorAutomatic`  
 Un valor RGB que especifica el automática color del botón predeterminado.  
  
 [in] `bEnable`  
 Especifica si el botón automático está habilitado o deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton  
 Habilitar o deshabilitar el botón "otro", que aparece debajo de los botones de color normal.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica el texto del botón.  
  
 [in] `bAltColorDlg`  
 Especifica si el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuando el usuario hace clic en el botón, se abre el cuadro de diálogo o el cuadro de diálogo de color de sistema.  
  
 [in] `bEnable`  
 Especifica si el botón "otro" está habilitado o deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Haga clic en el botón "otro" para mostrar un cuadro de diálogo color. Si el *bAltColorDlg* parámetro es `TRUE`, [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md) se muestra; en caso contrario, se muestra el cuadro de diálogo de color de sistema.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor  
 Recupera el color actual de automático (predeterminado).  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB que representa el color automático actual.  
  
### <a name="remarks"></a>Comentarios  
 Establece el color actual automática la [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) método.  
  
##  <a name="getcolor"></a>  CMFCColorButton::GetColor  
 Recupera el color seleccionado actualmente.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme  
 Indica si el botón de color actual se muestra en el estilo visual de Windows XP.  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si se admiten los estilos visuales y el botón de color actual se muestra en el estilo visual de Windows XP; en caso contrario, `FALSE`.  
  
##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode  
 Establece un botón de color en modo de personalización.  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si necesita agregar un botón de color a la página de una personalización del cuadro de diálogo (o permitir al usuario realizar otra selección de color durante la personalización), habilitar el botón estableciendo la `m_bEnabledInCustomizeMode` miembro `TRUE`. De forma predeterminada, este miembro está establecido en `FALSE`.  
  
##  <a name="ondraw"></a>  CMFCColorButton::OnDraw  
 Lo llama el marco de trabajo para representar una imagen del botón.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntos en el contexto de dispositivo que se usa para representar la imagen del botón.  
  
 [in] `rect`  
 Un rectángulo que delimita el botón.  
  
 [in] `uiState`  
 Especifica el estado visual del botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar el proceso de representación.  
  
##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder  
 Lo llama el marco de trabajo para mostrar el borde del botón.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Apunta al contexto de dispositivo utilizado para dibujar el borde.  
  
 [in] `rectClient`  
 Un rectángulo en el contexto de dispositivo especificado por el el `pDC` parámetro que define los límites del botón que se va a dibujar.  
  
 [in] `uiState`  
 Especifica el estado visual del botón.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para personalizar la apariencia del borde del botón de color.  
  
##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect  
 Lo llama el marco para mostrar un rectángulo de foco cuando el botón tiene el foco.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Apunta al contexto de dispositivo utilizado para dibujar el rectángulo de foco.  
  
 [in] `rectClient`  
 Un rectángulo en el contexto de dispositivo especificado por el `pDC` parámetro que define los límites del botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar el aspecto del rectángulo de foco.  
  
##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup  
 Se llama antes de que se muestre la barra de colores emergente.  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette  
 Inicializa el `m_pPalette` protegido miembro de datos a la paleta especificada o la paleta del sistema de forma predeterminada.  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pPal`|Un puntero a una paleta lógica o `NULL`. Si `NULL`, se usa la paleta del sistema de forma predeterminada.|  
  
##  <a name="setcolor"></a>  CMFCColorButton::SetColor  
 Especifica el color del botón.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un valor RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName  
 Especifica el nombre de un color.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 El valor del color RGB.  
  
 [in] `strName`  
 Nombre del color.  
  
### <a name="remarks"></a>Comentarios  
 La lista de nombres de colores es global por aplicación. Por lo tanto, este método transfiere sus parámetros a [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber  
 Define el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección de color del usuario.  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumns`  
 Especifica el número de columnas.  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede seleccionar un color de una barra de colores emergente que muestra una tabla de colores predefinidos. Utilice este método para definir el número de columnas de la tabla.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors  
 Especifica un conjunto de colores y el nombre del conjunto. El conjunto de colores se muestra con un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica la etiqueta que se mostrará con el conjunto de colores del documento.  
  
 [in] `lstColors`  
 Una referencia a una lista de los valores RGB.  
  
### <a name="remarks"></a>Comentarios  
 A `CMFCColorButton` objeto mantiene una lista de los valores RGB se transfieren a un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto. Cuando se muestra la barra de colores, estos colores se muestran en una sección especial cuya etiqueta es especificado por el `lpszLabel` parámetro.  
  
##  <a name="setpalette"></a>  CMFCColorButton::SetPalette  
 Especifica los colores estándares que se mostrará en la barra de colores emergente.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPalette`  
 Un puntero a una paleta de colores.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent  
 Cambia el tamaño del control de botón para ajustar su texto e imagen.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bCalcOnly`  
 Si es distinto de cero, se calcula el nuevo tamaño del control de botón, pero no se cambia el tamaño real.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que especifica un nuevo tamaño del control de botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor  
 Llamado por el marco de trabajo cuando el usuario selecciona un color en la barra de colores que se muestra cuando el usuario hace clic en el botón de color.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un color seleccionado por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 El `UpdateColor` función cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un `WM_COMMAND` de mensajes con un `BN_CLICKED` notificación estándar. Use la [CMFCColorButton::GetColor](#getcolor) método para recuperar el color seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCButton](../../mfc/reference/cmfcbutton-class.md)   
 [Clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette (clase)](../../mfc/reference/cpalette-class.md)   
 [CArray (clase)](../../mfc/reference/carray-class.md)   
 [CList (clase)](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)
