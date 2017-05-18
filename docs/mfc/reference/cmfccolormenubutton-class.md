---
title: Clase CMFCColorMenuButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton class
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
caps.latest.revision: 29
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: b6f7ddd5eb0b9c19b88f3c42b3ce7049a6d2ac3c
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="cmfccolormenubutton-class"></a>Clase CMFCColorMenuButton
La `CMFCColorMenuButton` clase es compatible con un comando de menú o un botón de barra de herramientas que se inicia un cuadro de diálogo de selector de color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Construye un objeto `CMFCColorMenuButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" que se coloca encima de los botones de color normal. (El botón automático estándar del sistema tiene la etiqueta **automática**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Permite la presentación de colores específicos del documento en lugar de colores del sistema.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otras" que se coloca debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otros" botón **más colores**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Habilita la capacidad de arrancar un panel de color.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automática actual.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Recupera el color del botón actual.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Recupera el color que se corresponde con un identificador de comando especificado.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando cambia la ventana primaria.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de selección de color.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Establece el color del botón de color actual.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Establece el color del botón de menú de color especificado.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Establece un nuevo nombre para el color especificado.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas que se muestran por un `CMFCColorBar` objeto.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Copia otro botón de barra de herramientas en el botón actual.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crea un cuadro de diálogo de selector de color.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indica si se admiten los menús vacíos.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para mostrar una imagen en un botón.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Lo llama el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Para reemplazar el botón de barra de herramientas o comandos de menú original con un `CMFCColorMenuButton` , cree el `CMFCColorMenuButton` objeto, establezca cualquier apropiada [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) estilos y, después, llame el `ReplaceButton` método de la [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) clase. Si personaliza una barra de herramientas, llame a la [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) método.  
  
 El cuadro de diálogo de selector de color se crea durante el procesamiento de la [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) controlador de eventos. El controlador de eventos notifica el marco primario con un `WM_COMMAND` mensaje. La `CMFCColorMenuButton` objeto envía el identificador del control que se asigna para el botón de barra de herramientas o comandos de menú original.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear y configurar un botón de menú de color mediante el uso de varios métodos en la `CMFCColorMenuButton` clase. En el ejemplo, un `CPalette` objeto se crea por primera vez y, a continuación, se utiliza para construir un objeto de la `CMFCColorMenuButton` clase. El `CMFCColorMenuButton` habilitar su automático y otros botones y establecer su color y el número de columnas, a continuación, configura el objeto. Este código forma parte de la [ejemplo de WordPad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad Nº 5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad #6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolormenubutton.h  
  
##  <a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton  
 Construye un objeto `CMFCColorMenuButton`.  
  
```  
CMFCColorMenuButton();

 
CMFCColorMenuButton(
    UINT uiCmdID,  
    LPCTSTR lpszText,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Un identificador de comando de botón.  
  
 [in] `lpszText`  
 El texto del botón.  
  
 [in] `pPalette`  
 Un puntero a la paleta de colores del botón.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor es el constructor predeterminado. El color del objeto actual y color automático se inicializan en negro (RGB (0, 0, 0)).  
  
 El segundo constructor inicializa el botón en el color que se corresponde con el identificador del comando especificado.  
  
##  <a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom  
 Copia una [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md)-objeto derivado a otro.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Botón de origen para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para copiar los objetos que se derivan de la `CMFCColorMenuButton` objeto.  
  
##  <a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu  
 Crea un cuadro de diálogo de selector de color.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto que representa un cuadro de diálogo de selector de color.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario presiona un botón de menú de color.  
  
##  <a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton  
 Habilita y deshabilita un botón "automático" que se coloca encima de los botones de color normal. (El botón automático estándar del sistema tiene la etiqueta **automática**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica el texto del botón que se muestra cuando el botón se convierte en automático.  
  
 [in] `colorAutomatic`  
 Especifica un nuevo color automático.  
  
 [in] `bEnable`  
 Especifica si el botón es automático o no.  
  
### <a name="remarks"></a>Comentarios  
 El botón automático aplica el color predeterminado actual.  
  
##  <a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors  
 Permite la presentación de colores específicos del documento en lugar de colores del sistema.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica el texto del botón.  
  
 [in] `bEnable`  
 `TRUE`para mostrar colores específicos del documento o `FALSE` para mostrar colores del sistema.  
  
### <a name="remarks"></a>Comentarios  
 Use este método para mostrar los colores del documento actual o la paleta de colores de sistema cuando el usuario hace clic en un botón de menú de color.  
  
##  <a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton  
 Habilita y deshabilita un botón "otras" que se coloca debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otros" botón **más colores**.)  
  
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
 Especifique `TRUE` para mostrar la `CMFCColorDialog` cuadro de diálogo, o `FALSE` para mostrar el cuadro de diálogo de color de sistema estándar.  
  
 [in] `bEnable`  
 Especifique `TRUE` para mostrar el botón "otro"; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff  
 Habilita la capacidad de arrancar un panel de color.  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 Especifica el identificador para el panel desplazable.  
  
 [in] `nVertDockColumns`  
 Especifica el número de columnas en el panel acoplado verticalmente color mientras está en estado desplazable.  
  
 [in] `nHorzDockRows`  
 Especifica el número de filas para el panel acoplado horizontalmente color mientras está en estado desplazable.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar la característica "desplazable" para el panel de color que aparece cuando el `CMFCColorMenuButton` se presiona el botón.  
  
##  <a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor  
 Recupera el color automática actual.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB que representa el color automática actual.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para obtener el color automático establecido por [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="getcolor"></a>CMFCColorMenuButton::GetColor  
 Recupera el color del botón actual.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color del botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID  
 Recupera el color que se corresponde con un identificador de comando especificado.  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Un identificador de comando.  
  
### <a name="return-value"></a>Valor devuelto  
 El color que se corresponde con el identificador del comando especificado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método cuando tiene varios botones de color en una aplicación. Cuando el usuario hace clic en un botón de color, el botón envía su identificador de comando en un `WM_COMMAND` mensaje a su elemento primario. El `GetColorByCmdID` método utiliza el identificador de comando para recuperar el color correspondiente.  
  
##  <a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed  
 Indica si se admiten los menús vacíos.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se permiten menús vacíos; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Menús vacíos se admiten de forma predeterminada. Invalide este método para cambiar este comportamiento en la clase derivada.  
  
##  <a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd  
 Lo llama el marco cuando cambia la ventana primaria.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Un puntero a la nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>CMFCColorMenuButton::OnDraw  
 Lo llama el marco de trabajo para mostrar una imagen en un botón.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que delimita el área que se vuelva a dibujar.  
  
 [in] `pImages`  
 Apunta a una lista de imágenes de barra de herramientas.  
  
 [in] `bHorz`  
 `TRUE`para especificar que la barra de herramientas está en un estado acoplado horizontal; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] `bCustomizeMode`  
 `TRUE`para especificar que la aplicación está en modo de personalización; en caso contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
 [in] `bHighlight`  
 `TRUE`para especificar que se resalta el botón; en caso contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
 [in] `bDrawBorder`  
 `TRUE`para especificar que se muestra el borde del botón; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`para especificar que deshabilitar botones están deshabilitados (atenuados); en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList  
 Lo llama el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que delimita el botón para dibujar.  
  
 [in] `bSelected`  
 `TRUE`Especifica que el botón está en estado seleccionado; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del botón.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un `CMFCColorMenuButton` objeto se muestra en el cuadro de lista durante el proceso de personalización de la barra de herramientas.  
  
##  <a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog  
 Abre un cuadro de diálogo de selección de color.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `colorDefault`  
 El color predeterminado que está seleccionado en el cuadro de diálogo color.  
  
 [out] `colorRes`  
 Devuelve el color que el usuario selecciona en el cuadro de diálogo color.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario selecciona un color nuevo; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se hace clic en el botón de menú, llame a este método para abrir un cuadro de diálogo color. Si el valor devuelto es distinto de cero, el color que el usuario selecciona se almacena en la `colorRes` parámetro. Use la [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) método para cambiar entre el cuadro de diálogo de colores estándar y la [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo.  
  
##  <a name="setcolor"></a>CMFCColorMenuButton::SetColor  
 Establece el color del botón de color actual.  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clr`  
 Un valor de color RGB.  
  
 [in] `bNotify`  
 `TRUE`Para aplicar el `clr` color de parámetro a cualquier botón de menú asociado o un botón de barra de herramientas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para cambiar el color del botón de color actual. Si el `bNotify` parámetro es distinto de cero, se cambia el color del botón correspondiente en la barra de herramientas ni menú emergente asociado al color especificado por el `clr` parámetro.  
  
##  <a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID  
 Establece el color del botón de menú de color especificado.  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 El identificador de recurso de un botón de menú de color.  
  
 [in] `color`  
 Un valor de color RGB.  
  
##  <a name="setcolorname"></a>CMFCColorMenuButton::SetColorName  
 Establece un nuevo nombre para el color especificado.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 El valor RGB del color cuyo nombre cambia.  
  
 [in] `strName`  
 El nuevo nombre del color.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber  
 Establece el número de columnas que se muestran en un control de selección de color ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objeto).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumns`  
 El número de columnas que desea mostrar.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton (clase)](../../mfc/reference/cmfccolorbutton-class.md)

