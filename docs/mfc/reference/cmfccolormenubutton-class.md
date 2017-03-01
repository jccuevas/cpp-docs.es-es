---
title: Clase CMFCColorMenuButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a9b1e7a3dbfe4d98b3d51850723eb22ec1f9da06
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolormenubutton-class"></a>Clase CMFCColorMenuButton
La `CMFCColorMenuButton` clase admite un comando de menú o un botón de barra de herramientas que inicia un cuadro de diálogo Selector de colores.  
  
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
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" que está situado encima de los botones de color normal. (El botón automático del sistema estándar se llama **automática**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Permite la visualización de colores específicos del documento en lugar de los colores del sistema.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otras" que se encuentra debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otro" botón **más colores... **.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permite arrancar un panel de color.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Recupera el color del botón actual.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Recupera el color que se corresponde con un identificador de comando especificado.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando cambia la ventana primaria.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de selección de color.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Establece el color del botón de color actual.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Establece el color del botón de menú de color especificado.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Establece un nuevo nombre para el color especificado.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas que se muestran por un `CMFCColorBar` objeto.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Copia otro botón de barra de herramientas en el botón actual.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crea un cuadro de diálogo Selector de colores.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indica si se admiten los menús vacíos.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para mostrar una imagen en un botón.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Llamado por el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Para reemplazar el botón de barra de herramientas o comandos de menú original con un `CMFCColorMenuButton` , cree el `CMFCColorMenuButton` objeto, establezca los correspondiente [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) estilos y, a continuación, llame el `ReplaceButton` método de la [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) clase. Si personaliza una barra de herramientas, llame a la [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) método.  
  
 El cuadro de diálogo Selector de colores se crea durante el procesamiento de la [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) controlador de eventos. El controlador de eventos notifica el marco primario con un `WM_COMMAND` mensaje. La `CMFCColorMenuButton` objeto envía el identificador de control que se asigna para el botón de barra de herramientas o comandos de menú original.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear y configurar un botón de menú de color mediante varios métodos en la `CMFCColorMenuButton` clase. En el ejemplo, un `CPalette` objeto se crea por primera vez y, a continuación, se utiliza para construir un objeto de la `CMFCColorMenuButton` clase. El `CMFCColorMenuButton` habilitar su automático y otros botones y establecer el color y el número de columnas, a continuación, configura el objeto. Este código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad&#5;](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad Nº&6;](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolormenubutton.h  
  
##  <a name="a-namecmfccolormenubuttona--cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton  
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
 Un identificador de comando del botón.  
  
 [in] `lpszText`  
 El texto del botón.  
  
 [in] `pPalette`  
 Puntero a la paleta de colores del botón.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor es el constructor predeterminado. El color del objeto actual y color automático se inicializan en negro (RGB (0, 0, 0)).  
  
 El segundo constructor inicializa el botón en el color que se corresponde con el identificador del comando especificado.  
  
##  <a name="a-namecopyfroma--cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom  
 Copia una [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md)-objeto derivado a otro.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Botón de origen para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para copiar los objetos que se derivan de la `CMFCColorMenuButton` objeto.  
  
##  <a name="a-namecreatepopupmenua--cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu  
 Crea un cuadro de diálogo Selector de colores.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto que representa un cuadro de diálogo Selector de colores.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario presiona un botón de menú de color.  
  
##  <a name="a-nameenableautomaticbuttona--cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton  
 Habilita y deshabilita un botón "automático" que está situado encima de los botones de color normal. (El botón automático del sistema estándar se llama **automática**.)  
  
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
  
##  <a name="a-nameenabledocumentcolorsa--cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors  
 Permite la visualización de colores específicos del documento en lugar de los colores del sistema.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 Especifica el texto del botón.  
  
 [in] `bEnable`  
 `TRUE`para mostrar colores específicos del documento o `FALSE` para mostrar los colores del sistema.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para mostrar los colores del documento actual o los colores de paleta del sistema cuando el usuario hace clic en un botón de menú de color.  
  
##  <a name="a-nameenableotherbuttona--cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton  
 Habilita y deshabilita un botón "otras" que se encuentra debajo de los botones de color normal. (El sistema estándar que tiene la etiqueta "otro" botón **más colores... **.)  
  
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
 Especifique `TRUE` para mostrar la `CMFCColorDialog` cuadro de diálogo, o `FALSE` para mostrar el cuadro de diálogo de colores estándar del sistema.  
  
 [in] `bEnable`  
 Especifique `TRUE` para mostrar el botón "other"; de lo contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenabletearoffa--cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff  
 Permite arrancar un panel de color.  
  
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
 Llamar a este método para habilitar la característica "divisibles" para el panel de color que aparece cuando el `CMFCColorMenuButton` está presionado.  
  
##  <a name="a-namegetautomaticcolora--cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor  
 Recupera el color automático actual.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB que representa el color automático actual.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para obtener el color automático establecido por [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="a-namegetcolora--cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor  
 Recupera el color del botón actual.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color del botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcolorbycmdida--cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID  
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
 Utilice este método cuando hay varios botones de color en una aplicación. Cuando el usuario hace clic en un botón de color, el botón envía su identificador de comando en un `WM_COMMAND` mensaje a su elemento primario. El `GetColorByCmdID` método utiliza el identificador de comando para recuperar el color correspondiente.  
  
##  <a name="a-nameisemptymenualloweda--cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed  
 Indica si se admiten los menús vacíos.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se permiten menús vacíos; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Menús vacíos se admiten de forma predeterminada. Invalide este método para cambiar este comportamiento en la clase derivada.  
  
##  <a name="a-nameonchangeparentwnda--cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd  
 Llamado por el marco de trabajo cuando cambia la ventana primaria.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Puntero a la nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawa--cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw  
 Llamado por el marco de trabajo para mostrar una imagen en un botón.  
  
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
 Un rectángulo que delimita el área se vuelva a dibujar.  
  
 [in] `pImages`  
 Apunta a una lista de imágenes de la barra de herramientas.  
  
 [in] `bHorz`  
 `TRUE`para especificar que la barra de herramientas está en un estado acoplado horizontal; de lo contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] `bCustomizeMode`  
 `TRUE`para especificar que la aplicación está en modo de personalización; de lo contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
 [in] `bHighlight`  
 `TRUE`para especificar que el botón está resaltado; de lo contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
 [in] `bDrawBorder`  
 `TRUE`para especificar que se muestra el borde del botón; de lo contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`para especificar que deshabilitar botones aparecen en gris (atenuado) de lo contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawoncustomizelista--cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList  
 Llamado por el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.  
  
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
 Un rectángulo que delimita el botón que se va a dibujar.  
  
 [in] `bSelected`  
 `TRUE`Especifica que el botón está seleccionado; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del botón.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un `CMFCColorMenuButton` objeto se muestra en el cuadro de lista durante el proceso de personalización de la barra de herramientas.  
  
##  <a name="a-nameopencolordialoga--cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog  
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
 Distinto de cero si el usuario selecciona un color nuevo; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se hace clic en el botón de menú, llame a este método para abrir un cuadro de diálogo color. Si el valor devuelto es distinto de cero, el color que selecciona el usuario se almacena en el `colorRes` parámetro. Utilice la [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) método para cambiar entre el cuadro de diálogo de colores estándar y la [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo.  
  
##  <a name="a-namesetcolora--cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor  
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
 `TRUE`Para aplicar el `clr` color de parámetro para cualquier botón de menú asociado o un botón de barra de herramientas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para cambiar el color del botón de color actual. Si el `bNotify` parámetro es distinto de cero, se cambia el color del botón en cualquier menú emergente asociada o la barra de herramientas correspondiente al color especificado por el `clr` parámetro.  
  
##  <a name="a-namesetcolorbycmdida--cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID  
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
  
##  <a name="a-namesetcolornamea--cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName  
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
  
##  <a name="a-namesetcolumnsnumbera--cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber  
 Establece el número de columnas que se muestran en un control de selección de color ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objeto).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumns`  
 El número de columnas para mostrar.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [Clase CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)

