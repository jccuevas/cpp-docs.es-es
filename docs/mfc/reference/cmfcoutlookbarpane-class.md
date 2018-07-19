---
title: CMFCOutlookBarPane (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81087eb5f611edd5ad41725177226c2c2b7a9c2d
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851354"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane (clase)
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Un control derivado de [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md) que puede insertarse en una barra de Outlook ( [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)). El panel de barra de Outlook contiene una columna de botones grandes. El usuario puede subir y bajar la lista de botones si es mayor que el panel. Cuando el usuario desasocia un panel de barra de Outlook de la barra de Outlook, puede flotar o acoplarse en la ventana de marco principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructor predeterminado.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|Agrega un botón en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Determina si se puede acoplar el panel a otra panel o ventana de marco. (Invalida [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización. (Invalida [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Crea el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCOutlookBarPane::Dock`|Lo llama el marco para acoplar el panel de la barra de Outlook. (Invalida `CPane::Dock`).|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzar la lista de botones de página o el botón.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Devuelve el color del texto normal (no seleccionado) del panel de barra de Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Determina si hay una imagen de fondo que se cargan para el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::IsChangeState`|Determina si se puede acoplar un panel flotante. (Invalida `CPane::IsChangeState`).|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Lo llama el marco cuando un panel se acerca a float. (Invalida [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Quita el botón que tiene un identificador de comando especificado.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaura el estado original de una barra de herramientas. (Invalida [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Establece el color de fondo.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Establece la imagen de fondo.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Restablece el panel de la barra de Outlook en el conjunto original de botones.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Establece el número de píxeles de relleno usado en torno a los botones en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Establece el color transparente para el panel de la barra de Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Se usa internamente para actualizar la barra de Outlook. (Invalida `CMFCToolBar::SmartUpdate`).|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Especifica qué elementos del menú contextual que se muestran en el modo de personalización.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Quita todos los botones en el panel de la barra de Outlook. (Invalida [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información sobre cómo implementar una barra de Outlook, consulte [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Para obtener un ejemplo de una barra de Outlook, consulte el proyecto de ejemplo OutlookDemo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos de la `CMFCOutlookBarPane` clase. El ejemplo muestra cómo crear un panel de barra de Outlook, habilitar el modo de desplazamiento de página, habilite el acoplamiento y establecer el color de fondo de la barra de Outlook. Este fragmento de código forma parte de la [ejemplo Outlook con varias vistas](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
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
  
##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton  
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
 [in] *uiImage*  
 Especifica el identificador de recurso de un mapa de bits.  
  
 [in] *lpszLabel*  
 Especifica el texto del botón.  
  
 [in] *iIdCommand*  
 Especifica el identificador. del control de botón  
  
 [in] *iInsertAt*  
 Especifica el índice de base cero en la página de la barra de outlook en el que se va a insertar el botón.  
  
 [in] *uiLabel*  
 Un identificador de recurso de cadena.  
  
 [in] *szBmpFileName*  
 Especifica el nombre del archivo de imagen de disco para cargar.  
  
 [in] *szLabel*  
 Especifica el texto del botón.  
  
 [in] *hBmp*  
 Identificador de mapa de bits de un botón.  
  
 [in] *hIcon*  
 Identificador de un icono de los botones.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si un botón se ha agregado correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para insertar un nuevo botón en la página de la barra de Outlook. La imagen del botón se puede cargar desde los recursos de aplicación o desde un archivo de disco.  
  
 Si el Id. de página especificado por *uiPageID* es -1, el botón se inserta en la primera página.  
  
 Si el índice especificado por *iInsertAt* es -1, el botón se agrega al final de la página.  
  
##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll  
 Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método llama directamente a [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), que se llama en las imágenes que se usan el panel de barra de Outlook.  
  
##  <a name="create"></a>  CMFCOutlookBarPane::Create  
 Crea el panel de la barra de Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParentWnd*  
 Especifica la ventana primaria del control del panel de barra de Outlook. No debe ser NULL.  
  
 [in] *dwStyle*  
 Nombre del estilo de la ventana.  Para obtener una lista de estilos de ventana, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *uiID*  
 El identificador de control. Debe ser único para habilitar el almacenamiento de estado del control.  
  
 [in] *dwControlBarStyle*  
 Especifica los estilos especiales que definen el comportamiento del control del panel de barra de Outlook cuando se separa de la barra de Outlook.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Para construir un `CMFCOutlookBarPane` objeto, llame primero al constructor y, a continuación, llame a `Create`, que crea el control de panel de la barra de Outlook y lo adjunta a la `CMFCOutlookBarPane` objeto.  
  
 Para obtener más información acerca de `dwControlBarStyle` vea [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems  
 Especifica qué elementos del menú contextual que se muestran en el modo de personalización.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
 Un puntero a un botón de barra de herramientas que un usuario ha seleccionado.  
  
 [in] *pPopup*  
 Un puntero al menú contextual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se debería mostrar el menú contextual; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para modificar el marco de trabajo estándar acceso directo que muestra el marco de trabajo en el modo de personalización.  
  
 La implementación predeterminada comprueba el modo de personalización ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) y si se establece en TRUE, deshabilita todo el método abreviado de los elementos de menú excepción **eliminar**. A continuación, simplemente pasa los parámetros de entrada a `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Menú contextual* es un sinónimo de menú contextual.  
  
##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode  
 Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzar a la lista de botones de página por página o mediante el botón.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bPageScroll*  
 Si es TRUE, habilitar el modo de desplazamiento de página. Si es FALSE, deshabilite el modo de desplazamiento de página.  
  
##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor  
 Devuelve la normal (es decir, no se han seleccionado) color del texto del panel de barra de Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Color del texto actual como un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Use [CMFCOutlookBarPane::SetTextColor](#settextcolor) para establecer el color de texto (normales y seleccionado) actual de la barra de Outlook. Puede obtener el color de texto mediante una llamada a la [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) función con el índice COLOR_WINDOW.  
  
##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture  
 Determina si hay una imagen de fondo que se cargan para el panel de la barra de Outlook.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si existe una imagen de fondo para mostrar; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Puede agregar una imagen de fondo mediante una llamada a [CMFCOutlookBarPane::SetBackImage](#setbackimage) función.  
  
 Si no hay ninguna imagen de fondo, se pinta el fondo con un color especificado mediante el uso de [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight  
 Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si los bordes del botón están sombreados; en caso contrario, FALSE.  
  
##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons  
 Quita todos los botones en el panel de la barra de Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton  
 Quita el botón que tiene un identificador de comando especificado.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iIdCommand*  
 Especifica el identificador de comando de un botón para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón se ha quitado correctamente; FALSE si el identificador de comando especificado no es válido.  
  
##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor  
 Establece el color de fondo de la barra de Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *color*  
 Especifica el nuevo color de fondo.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer el color de fondo actual de la barra de Outlook. El color de fondo se usa solo si no hay ninguna imagen de fondo.  
  
##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage  
 Establece la imagen de fondo.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *uiImageID*  
 Especifica el identificador de recurso de imagen.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer la Outlook imagen de fondo de la barra. La lista de imágenes de fondo es administrada por el objeto incrustado [CMFCToolBarImages (clase)](../../mfc/reference/cmfctoolbarimages-class.md) objeto.  
  
##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState  
 Restablece el panel de la barra de Outlook en el conjunto original de botones.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método restaura los botones de barra de Outlook en el conjunto original. Este método es similar a `CMFCOutlookBarPane::RestoreOriginalstate`, salvo que no desencadena una actualización del panel de barra de Outlook.  
  
##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace  
 Establece el número de píxeles de relleno usado en torno a los botones en el panel de la barra de Outlook.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor  
 Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *clrRegText*  
 Especifica el nuevo color de texto no seleccionado.  
  
 [in] *clrSelText*  
 Especifica el nuevo color para el texto seleccionado.  
  
##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor  
 Establece el color transparente para el panel de la barra de Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 *Color*  
 Especifica el nuevo color transparente.  
  
### <a name="remarks"></a>Comentarios  
 Color transparente se requiere para mostrar imágenes transparentes. Cualquier aparición de este color en una imagen se pinta con el color de fondo en su lugar.  No hay ninguna mezcla de imágenes de fondo y primer plano.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl (clase)](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
