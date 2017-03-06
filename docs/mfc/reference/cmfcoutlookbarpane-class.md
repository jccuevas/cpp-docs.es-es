---
title: Clase CMFCOutlookBarPane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
dev_langs:
- C++
helpviewer_keywords:
- Dock method
- IsChangeState method
- SmartUpdate method
- OnBeforeFloat method
- RestoreOriginalstate method
- CMFCOutlookBarPane class
- CanBeRestored method
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: 30
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
ms.openlocfilehash: da4fab1a6d94e962090f21414062dc2da0c9482c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbarpane-class"></a>Clase CMFCOutlookBarPane
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Un control derivado de [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) que se pueden insertar en una barra de Outlook ( [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md)). El panel de barra de Outlook contiene una columna de botones grandes. El usuario puede subir y bajar la lista de botones si es mayor que el panel. Cuando el usuario desasocia un panel de barra de Outlook de la barra de Outlook, puede flotar o acoplarse en la ventana de marco principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructor predeterminado.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|Agrega un botón en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Determina si el panel se puede acoplar a otra ventana de panel o marco. (Invalida [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización. (Invalida [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Crea el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCOutlookBarPane::Dock`|Llamado por el marco para acoplar el panel de la barra de Outlook. (Invalida `CPane::Dock`).|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzar la lista de botones de página o el botón.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Devuelve el color de texto normal (no seleccionado) del panel de barra de Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Determina si hay una imagen de fondo que se cargan para el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::IsChangeState`|Determina si se puede acoplar un panel flotante. (Invalida `CPane::IsChangeState`).|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Determina si el borde del botón está atenuado cuando un botón se resalta y se muestra una imagen de fondo.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Lo llama el marco de trabajo cuando se trata de un panel a float. (Invalida [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Quita el botón que tiene un identificador de comando especificado.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaura el estado original de una barra de herramientas. (Invalida [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Establece el color de fondo.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Establece la imagen de fondo.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Restablece el panel de la barra de Outlook en el conjunto original de botones.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Establece el número de píxeles de relleno usado en torno a botones en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Establece el color transparente para el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Se usa internamente para actualizar la barra de Outlook. (Invalida `CMFCToolBar::SmartUpdate`).|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Especifica qué elementos de menú contextual se muestran en el modo de personalización.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Quita todos los botones en el panel de la barra de Outlook. (Invalida [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información sobre cómo implementar una barra de Outlook, consulte [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Para obtener un ejemplo de una barra de Outlook, consulte el proyecto de ejemplo de OutlookDemo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos de la `CMFCOutlookBarPane` clase. En el ejemplo se muestra cómo crear un panel de barra de Outlook, habilitar el modo de desplazamiento de página, habilite el acoplamiento y establecer el color de fondo de la barra de Outlook. Este fragmento de código forma parte de la [ejemplo Outlook múltiples vistas](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews&3;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews Nº&4;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxoutlookbarpane.h  
  
##  <a name="a-nameaddbuttona--cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton  
 Agrega un botón en el panel de la barra de Outlook.  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiImage`  
 Especifica el identificador de recursos de un mapa de bits.  
  
 [in] `lpszLabel`  
 Especifica el texto del botón.  
  
 [in] `iIdCommand`  
 Especifica el identificador. del control de botón  
  
 [in] `iInsertAt`  
 Especifica el índice de base cero en la página de la barra de outlook en el que se va a insertar el botón.  
  
 [in] `uiLabel`  
 Un identificador de recurso de cadena.  
  
 [in] `szBmpFileName`  
 Especifica el nombre del archivo de imagen de disco para cargar.  
  
 [in] `szLabel`  
 Especifica el texto del botón.  
  
 [in] `hBmp`  
 Identificador de mapa de bits del botón.  
  
 [in] `hIcon`  
 Identificador de un icono de un botones.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un botón se ha agregado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para insertar un nuevo botón en la página de la barra de Outlook. La imagen del botón se puede cargar desde los recursos de aplicación o desde un archivo de disco.  
  
 Si el identificador de página especificado por `uiPageID` es -1, el botón se inserta en la primera página.  
  
 Si el índice especificado por `iInsertAt` es -1, el botón se agrega al final de la página.  
  
##  <a name="a-namecanbeattacheda--cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameclearalla--cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll  
 Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método llama directamente a [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), que se llama en las imágenes que se utilizan en el panel de la barra de Outlook.  
  
##  <a name="a-namecreatea--cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Create  
 Crea el panel de la barra de Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Especifica la ventana primaria del control de panel de la barra de Outlook. No debe ser `NULL`.  
  
 [in] `dwStyle`  
 Nombre del estilo de la ventana.  Para obtener una lista de estilos de ventana, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `uiID`  
 El identificador del control. Debe ser único para permitir guardar el estado del control.  
  
 [in] `dwControlBarStyle`  
 Especifica los estilos especiales que definen el comportamiento del control de panel de barra de Outlook cuando se separa de la barra de Outlook.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para construir un `CMFCOutlookBarPane` objeto, llame primero al constructor y, a continuación, llame a `Create`, que crea el control de panel de la barra de Outlook y lo adjunta a la `CMFCOutlookBarPane` objeto.  
  
 Para obtener más información acerca de `dwControlBarStyle` vea [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="a-nameenablecontextmenuitemsa--cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems  
 Especifica qué elementos de menú contextual se muestran en el modo de personalización.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero a un botón de barra de herramientas que el usuario hizo clic.  
  
 [in] `pPopup`  
 Un puntero al menú contextual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si el menú contextual se debe mostrar; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para modificar el menú de método abreviado estándar de framework que el marco de trabajo se muestra en el modo de personalización.  
  
 La implementación predeterminada comprueba el modo de personalización ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) y si se establece en `TRUE`, deshabilita todos los elementos de menú contextual excepto **eliminar**. A continuación, simplemente pasa los parámetros de entrada `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Menú contextual* es un sinónimo de menú contextual.  
  
##  <a name="a-nameenablepagescrollmodea--cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode  
 Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzar la lista de botones de página por página o por el botón.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPageScroll`  
 Si `TRUE`, habilitar el modo de desplazamiento de la página. Si `FALSE`, deshabilitar el modo de desplazamiento de la página.  
  
##  <a name="a-namegetregularcolora--cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor  
 Devuelve la normal (es decir, no se han seleccionado) color del texto del panel de barra de Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de texto actual como un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CMFCOutlookBarPane::SetTextColor](#settextcolor) para establecer el color de texto (regular y seleccionado) actual de la barra de Outlook. Puede obtener el color de texto predeterminado llamando el [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) funciona con el `COLOR_WINDOW` índice.  
  
##  <a name="a-nameisbackgroundtexturea--cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture  
 Determina si hay una imagen de fondo que se cargan para el panel de la barra de Outlook.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no hay imagen de fondo para mostrar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede agregar una imagen de fondo llamando [CMFCOutlookBarPane::SetBackImage](#setbackimage) (función).  
  
 Si no hay ninguna imagen de fondo, se pinta el fondo con un color especificado mediante [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="a-nameisdrawshadedhighlighta--cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight  
 Determina si el borde del botón está atenuado cuando un botón se resalta y se muestra una imagen de fondo.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los bordes están sombreadas; de lo contrario, `FALSE`.  
  
##  <a name="a-nameremoveallbuttonsa--cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons  
 Quita todos los botones en el panel de la barra de Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="a-nameremovebuttona--cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton  
 Quita el botón que tiene un identificador de comando especificado.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIdCommand`  
 Especifica el identificador de comando de un botón para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón se ha quitado correctamente; `FALSE` si el identificador de comando especificado no es válido.  
  
##  <a name="a-namesetbackcolora--cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor  
 Establece el color de fondo de la barra de Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Especifica el nuevo color de fondo.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer el color de fondo actual de la barra de Outlook. El color de fondo se utiliza sólo si no hay ninguna imagen de fondo.  
  
##  <a name="a-namesetbackimagea--cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage  
 Establece la imagen de fondo.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiImageID`  
 Especifica el identificador de recurso de imagen.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para establecer el Outlook imagen de fondo de la barra. La lista de imágenes de fondo está administrada por el objeto incrustado [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto.  
  
##  <a name="a-namesetdefaultstatea--cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState  
 Restablece el panel de la barra de Outlook en el conjunto original de botones.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método restaura los botones de la barra de Outlook en el conjunto original. Este método es similar a `CMFCOutlookBarPane::RestoreOriginalstate`, excepto que no desencadena una actualización del panel de barra de Outlook.  
  
##  <a name="a-namesetextraspacea--cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace  
 Establece el número de píxeles de relleno usado en torno a botones en el panel de la barra de Outlook.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="a-namesettextcolora--cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor  
 Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrRegText`  
 Especifica el color para el texto no se han seleccionado.  
  
 [in] `clrSelText`  
 Especifica el nuevo color para el texto seleccionado.  
  
##  <a name="a-namesettransparentcolora--cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor  
 Establece el color transparente para el panel de la barra de Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 `color`  
 Especifica el nuevo color transparente.  
  
### <a name="remarks"></a>Comentarios  
 Color transparente es necesario para mostrar imágenes transparentes. Cualquier aparición de este color en una imagen se dibuja con el color de fondo en su lugar.  No hay ninguna combinación de imágenes de fondo y primer plano.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Clase CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

