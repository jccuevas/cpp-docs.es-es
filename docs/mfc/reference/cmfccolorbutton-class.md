---
title: Clase CMFCColorButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMFCColorButton::m_Color data member
- CMFCColorButton::m_bAutoSetFocus data member
- CMFCColorButton::m_pPopup data member
- CMFCColorButton::m_nColumns data member
- CMFCColorButton class
- CMFCColorButton::m_strAutoColorText data member
- CMFCColorButton::m_bAltColorDlg data member
- CMFCColorButton::m_strDocColorsText data member
- CMFCColorButton::m_strOtherText data member
- CMFCColorButton::m_pPalette data member
- CMFCColorButton::m_lstDocColors data member
- CMFCColorButton::m_ColorAutomatic data member
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: 34
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
ms.openlocfilehash: 6a9290d396c8ce5ccafa2ae556b21ff89806d830
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolorbutton-class"></a>Clase CMFCColorButton
El `CMFCColorButton` y [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) clases se utilizan conjuntamente para implementar un control de selector de color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construye un nuevo objeto `CMFCColorButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" que está situado encima de los botones de color normal. (El botón automático del sistema estándar se llama **automática**.)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otras" que se encuentra debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otro" botón **más colores... **.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|  
|[CMFCColorButton::GetColor](#getcolor)|Recupera el color del botón.|  
|[CMFCColorButton::SetColor](#setcolor)|Establece el color del botón.|  
|[CMFCColorButton::SetColorName](#setcolorname)|Establece un nombre de color.|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas en el cuadro de diálogo Selector de colores.|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Especifica una lista de colores específicos del documento que se muestran en el cuadro de diálogo Selector de colores.|  
|[CMFCColorButton::SetPalette](#setpalette)|Especifica una paleta de colores estándar.|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|Cambia el tamaño del control de botón, dependiendo de su tamaño de texto e imagen.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indica si el botón de color actual se muestra en el estilo visual de Windows XP.|  
|[CMFCColorButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para mostrar una imagen del botón.|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Llamado por el marco de trabajo para mostrar el borde del botón.|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco para mostrar un rectángulo de foco cuando el botón tiene un foco.|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Lo llama el marco de trabajo cuando el cuadro de diálogo Selector de colores se va a mostrar.|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializa el `m_pPalette` protegido el miembro de datos a la paleta especificada o en la paleta del sistema predeterminado.|  
|[CMFCColorButton::UpdateColor](#updatecolor)|Lo llama el marco de trabajo cuando el usuario selecciona un color de la paleta del cuadro de diálogo Selector de color.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`m_bAltColorDlg`|Un valor booleano. Si `TRUE`, el marco de trabajo muestra el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo de color cuando la *otros* se hace clic en el botón, o si `FALSE`, el cuadro de diálogo color de sistema. El valor predeterminado es `TRUE`. Para obtener más información, consulte [CMFCColorButton::EnableOtherButton](#enableotherbutton).|  
|`m_bAutoSetFocus`|Un valor booleano. Si `TRUE`, el marco de trabajo establece el foco en el menú de color cuando se muestre el menú, o si `FALSE`, no cambia el foco. El valor predeterminado es `TRUE`.|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indica si está habilitado el modo de personalización para el botón de color.|  
|`m_Color`|Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor. Contiene el color seleccionado actualmente.|  
|`m_ColorAutomatic`|Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor. Contiene el color predeterminado seleccionado actualmente.|  
|`m_Colors`|Un [CArray](../../mfc/reference/carray-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores. Contiene los colores disponibles actualmente.|  
|`m_lstDocColors`|Un [CList](../../mfc/reference/clist-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores. Contiene los colores del documento actual.|  
|`m_nColumns`|Entero. Contiene el número de columnas que se muestran en la cuadrícula de colores de un menú de selección de color.|  
|`m_pPalette`|Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md). Contiene los colores que están disponibles en el menú de selección de color actual.|  
|`m_pPopup`|Un puntero a un [CMFCColorPopupMenu clase](../../mfc/reference/cmfccolorpopupmenu-class.md) objeto. El menú de selección de color que se muestra al hacer clic en el botón de color.|  
|`m_strAutoColorText`|Una cadena. La etiqueta del botón "automático" en un menú de selección de color.|  
|`m_strDocColorsText`|Una cadena. La etiqueta del botón en un menú de selección de color que muestra los colores del documento.|  
|`m_strOtherText`|Una cadena. La etiqueta del botón "otro" en un menú de selección de color.|  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, la `CMFCColorButton` clase se comporta como un botón de comando que abre un cuadro de diálogo Selector de color. El cuadro de diálogo Selector de colores contiene una matriz de botones de color pequeño y un botón "otras" que muestra un selector de colores personalizados. (El sistema estándar que tiene la etiqueta "otro" botón **más colores... **.) Cuando un usuario selecciona un nuevo color, el `CMFCColorButton` objeto refleja el cambio y muestra el color seleccionado.  
  
 Crear un control de botón de color directamente en el código o mediante el **ClassWizard** herramienta y una plantilla de cuadro de diálogo. Si crea un control de botón de color directamente, agregar un `CMFCColorButton` variable a su aplicación y, a continuación, llame al constructor y `Create` métodos de la `CMFCColorButton` objeto. Si utiliza la **ClassWizard**, agregue un `CButton` variable a la aplicación y, a continuación, cambie el tipo de la variable de `CButton` a `CMFCColorButton`.  
  
 El cuadro de diálogo Selector de color ( [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md)) muestra el [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método cuando se llama el marco de la `OnLButtonDown` controlador de eventos. El [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método puede invalidarse para admitir la selección del color personalizado.  
  
 El `CMFCColorButton` objeto notifica a su elemento primario que está cambiando un color mediante el envío un `WM_COMMAND | BN_CLICKED` notificación. El elemento primario usa el [CMFCColorButton::GetColor](#getcolor) método para recuperar el color actual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un botón de color mediante varios métodos en la `CMFCColorButton` clase. Los métodos de establecer el color del botón de color y su número de columnas y habilitar automático y los otros botones. Este ejemplo forma parte de la [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo&#10;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo&#11;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton  
 Construye un nuevo objeto `CMFCColorButton`.  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton  
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
 Un valor RGB que especifica el color predeterminado de automático del botón.  
  
 [in] `bEnable`  
 Especifica si el botón automático está habilitado o deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton  
 Habilitar o deshabilitar el botón "other", que aparece debajo de los botones de color normal.  
  
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
 Especifica si la [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuando el usuario hace clic en el botón, se abre el cuadro de diálogo o el cuadro de diálogo color de sistema.  
  
 [in] `bEnable`  
 Especifica si el botón "otras" está habilitada o deshabilitada.  
  
### <a name="remarks"></a>Comentarios  
 Haga clic en el botón "otras" para mostrar un cuadro de diálogo color. Si el *bAltColorDlg* parámetro es `TRUE`, [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md) se muestra; en caso contrario, se muestra el cuadro de diálogo color de sistema.  
  
##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor  
 Recupera el color actual de automático (predeterminado).  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB que representa el color automático actual.  
  
### <a name="remarks"></a>Comentarios  
 Establece el color actual automática la [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) método.  
  
##  <a name="getcolor"></a>CMFCColorButton::GetColor  
 Recupera el color seleccionado actualmente.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme  
 Indica si el botón de color actual se muestra en el estilo visual de Windows XP.  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se admiten estilos visuales y el botón de color actual se muestra en el estilo visual de Windows XP; de lo contrario, `FALSE`.  
  
##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode  
 Un botón de color se establece en modo de personalización.  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si necesita agregar un botón de color a la página de una personalización del cuadro de diálogo (o permitir al usuario realizar otra selección de color durante la personalización), habilitar el botón estableciendo la `m_bEnabledInCustomizeMode` miembro `TRUE`. De forma predeterminada, este miembro se establece en `FALSE`.  
  
##  <a name="ondraw"></a>CMFCColorButton::OnDraw  
 Llamado por el marco de trabajo para procesar una imagen del botón.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Señala al contexto de dispositivo que se utiliza para representar la imagen del botón.  
  
 [in] `rect`  
 Un rectángulo que delimita el botón.  
  
 [in] `uiState`  
 Especifica el estado visual del botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar el proceso de representación.  
  
##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder  
 Llamado por el marco de trabajo para mostrar el borde del botón.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Señala al contexto de dispositivo utilizado para dibujar el borde.  
  
 [in] `rectClient`  
 Un rectángulo en el contexto de dispositivo especificado por del `pDC` parámetro que define los límites del botón que se va a dibujar.  
  
 [in] `uiState`  
 Especifica el estado visual del botón.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar la apariencia del borde del botón de color.  
  
##  <a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect  
 Llamado por el marco para mostrar un rectángulo de foco cuando el botón tiene el foco.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Señala al contexto de dispositivo utilizado para dibujar el rectángulo de foco.  
  
 [in] `rectClient`  
 Un rectángulo en el contexto de dispositivo especificado por el `pDC` parámetro que define los límites del botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar la apariencia del rectángulo de foco.  
  
##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup  
 Se llama antes de que se muestra la barra de color del menú emergente.  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette  
 Inicializa el `m_pPalette` protegido el miembro de datos a la paleta especificada o en la paleta del sistema predeterminado.  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pPal`|Un puntero a una paleta lógica o `NULL`. Si `NULL`, se usa la paleta del sistema predeterminado.|  
  
##  <a name="setcolor"></a>CMFCColorButton::SetColor  
 Especifica el color del botón.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un valor RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcolorname"></a>CMFCColorButton::SetColorName  
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
 La lista de nombres de colores es global por aplicación. Por consiguiente, este método transfiere sus parámetros a [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).  
  
##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber  
 Define el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección de color del usuario.  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumns`  
 Especifica el número de columnas.  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede seleccionar un color de una barra de colores de la ventana emergente que muestra una tabla de colores predefinidos. Utilice este método para definir el número de columnas de la tabla.  
  
##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors  
 Especifica un conjunto de colores y el nombre del conjunto. Se muestra el conjunto de colores mediante un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica la etiqueta que se mostrará con el conjunto de colores del documento.  
  
 [in] `lstColors`  
 Una referencia a una lista de valores RGB.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCColorButton` objeto mantiene una lista de los valores RGB se transfieren a un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto. Cuando se muestre la barra de colores, estos colores se muestran en una sección especial cuya etiqueta es especificado por el `lpszLabel` parámetro.  
  
##  <a name="setpalette"></a>CMFCColorButton::SetPalette  
 Especifica los colores estándares para mostrar en la barra de color del menú emergente.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPalette`  
 Puntero a una paleta de colores.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sizetocontent"></a>CMFCColorButton::SizeToContent  
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
  
##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor  
 Lo llama el marco de trabajo cuando el usuario selecciona un color en la barra de colores que se muestra cuando el usuario hace clic en el botón de color.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un color seleccionado por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 El `UpdateColor` función cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un `WM_COMMAND` de mensajes con un `BN_CLICKED` notificación estándar. Utilice la [CMFCColorButton::GetColor](#getcolor) método para recuperar el color seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCButton](../../mfc/reference/cmfcbutton-class.md)   
 [Clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette (clase)](../../mfc/reference/cpalette-class.md)   
 [CArray (clase)](../../mfc/reference/carray-class.md)   
 [CList (clase)](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)

