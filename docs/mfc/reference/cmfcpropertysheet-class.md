---
title: Clase de CMFCPropertySheet | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b61adc98f6b6e84f5e2ef10f88ae41720e2fbf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertysheet-class"></a>Clase de CMFCPropertySheet
La clase `CMFCPropertySheet` admite una hoja de propiedades donde cada página de propiedades se indica mediante una pestaña de página, un botón de barra de herramientas, un nodo del control de árbol o un elemento de lista.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Construye un objeto `CMFCPropertySheet`.|  
|`CMFCPropertySheet::~CMFCPropertySheet`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertySheet:: AddPage](#addpage)|Agrega una página a la hoja de propiedades.|  
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Agrega una nueva página de propiedades al control de árbol.|  
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Agrega un nuevo nodo al control de árbol.|  
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Reserva espacio en la parte superior de cada página para dibujar un encabezado personalizado.|  
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Recupera el alto del encabezado actual.|  
|[CMFCPropertySheet::GetLook](#getlook)|Recupera un valor de enumeración que especifica el aspecto de la hoja de propiedades actual.|  
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Recupera el ancho de la barra de navegación, en píxeles.|  
|[CMFCPropertySheet::GetTab](#gettab)|Recupera el objeto de control de la pestaña interna que admite el control de la hoja de propiedades actual.|  
|`CMFCPropertySheet::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializa el aspecto del control de la hoja de propiedades actual.|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Lo llama el marco de trabajo cuando se ha habilitado una página de propiedades.|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Lo llama el marco de trabajo para dibujar un encabezado de la página de propiedades personalizada.|  
|`CMFCPropertySheet::OnInitDialog`|Controla la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje. (Invalida [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Lo llama el marco de trabajo para quitar una página de propiedades de un control de árbol.|  
|`CMFCPropertySheet::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida `CPropertySheet::PreTranslateMessage`).|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Quita un nodo del control de árbol.|  
|[CMFCPropertySheet::RemovePage](#removepage)|Quita una página de propiedades de la hoja de propiedades.|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Especifica la lista de imágenes que se usan en el control de navegación del panel de Outlook.|  
|[CMFCPropertySheet:: Setlook](#setlook)|Especifica el aspecto de la hoja de propiedades.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CMFCPropertySheet` representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña. La clase `CMFCPropertySheet` puede mostrar una página de propiedades de varias formas.  
  
 Realice los pasos siguientes para usar la clase `CMFCPropertySheet` en la aplicación:  
  
1.  Derive una clase de la clase `CMFCPropertySheet` y llámela, por ejemplo, CMyPropertySheet.  
  
2.  Construir un [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) objeto para cada página de propiedades.  
  
3.  Llame a la [CMFCPropertySheet:: Setlook](#setlook) método del constructor CMyPropertySheet. Un parámetro de ese método especifica que las páginas de propiedades se mostrarán como pestañas a lo largo de la parte superior o izquierda de la hoja de propiedades, como pestañas en el estilo de una hoja de propiedades de Microsoft OneNote, como botones en un control de barra de herramientas de Microsoft Outlook, como nodos en un control de árbol o como una lista de elementos en el lado izquierdo de la hoja de propiedades.  
  
4.  Si crea una hoja de propiedades en el estilo de una barra de herramientas de Microsoft Outlook, llame a la [CMFCPropertySheet::SetIconsList](#seticonslist) método para asociar una lista de imágenes junto con las páginas de propiedades.  
  
5.  Llame a la [CMFCPropertySheet:: AddPage](#addpage) método para cada página de propiedades.  
  
6.  Cree un control `CMFCPropertySheet` y llame a su método `DoModal`.  
  
## <a name="illustrations"></a>Ilustraciones  
 La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de una barra de herramientas incrustada de Microsoft Outlook. La barra de herramientas de Outlook aparece en el lado izquierdo de la hoja de propiedades.  
  
 ![Controles de color de CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 La siguiente ilustración muestra una hoja de propiedades que contiene un [clase CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objeto. Ese objeto es una hoja de propiedades del estilo de una hoja de propiedades de controles comunes estándar.  
  
 ![Controles de propiedad y lista de CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de un control de árbol.  
  
 ![Árbol de propiedades](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertysheet.h  
  
##  <a name="addpage"></a>  CMFCPropertySheet:: AddPage  
 Agrega una página a la hoja de propiedades.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPage`  
 Puntero a un objeto de página. Este parámetro no puede ser `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega la página de propiedades especificado como la pestaña situada en la hoja de propiedades. Por lo tanto, utilice este método para agregar páginas en orden de izquierda a derecha.  
  
 Si la hoja de propiedades se encuentra en el estilo de Microsoft Outlook, el marco de trabajo muestra una lista de botones de navegación a la izquierda de la hoja de propiedades. Después de que este método agrega una página de propiedades, agrega un botón correspondiente a la lista. Para mostrar una página de propiedades, haga clic en su botón correspondiente. Para obtener más información sobre los estilos de hojas de propiedades, vea [CMFCPropertySheet:: Setlook](#setlook).  
  
##  <a name="addpagetotree"></a>  CMFCPropertySheet::AddPageToTree  
 Agrega una nueva página de propiedades al control de árbol.  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCategory`  
 Puntero a un nodo de árbol primario, o `NULL` para asociar el nodo de nivel superior en la página especificada. Llame a la [CMFCPropertySheet::AddTreeCategory](#addtreecategory) método para obtener este puntero.  
  
 [in] `pPage`  
 Puntero a un objeto de página de propiedades.  
  
 [in] `nIconNum`  
 Índice de base cero de un icono o -1 si no se usa ningún icono. El icono se muestra junto a la página de propiedades del control de árbol cuando la página no está seleccionada. El valor predeterminado es -1.  
  
 [in] `nSelIconNum`  
 Índice de base cero de un icono o -1 si no se usa ningún icono. Cuando se selecciona la página, se muestra el icono junto a la página de propiedades del control de árbol. El valor predeterminado es -1.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega una página de propiedades como una hoja de un control de árbol. Para agregar una página de propiedades, cree una `CMFCPropertySheet` objeto, llame a la [CMFCPropertySheet:: Setlook](#setlook) método con el `look` parámetro establecido en `CMFCPropertySheet::PropSheetLook_Tree`y, a continuación, use este método para agregar la página de propiedades.  
  
##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory  
 Agrega un nuevo nodo al control de árbol.  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 El nombre del nodo.  
  
 [in] `nIconNum`  
 Índice de base cero de un icono o -1 si no se usa ningún icono. El icono se muestra junto a la página de propiedades del control de árbol cuando la página no está seleccionada. El valor predeterminado es -1.  
  
 [in] `nSelectedIconNum`  
 Índice de base cero de un icono o -1 si no se usa ningún icono. Cuando se selecciona la página, se muestra el icono junto a la página de propiedades del control de árbol. El valor predeterminado es -1.  
  
 [in] `pParentCategory`  
 Puntero a un nodo de árbol primario, o `NULL` para asociar el nodo de nivel superior en la página especificada. Establezca este parámetro con el [CMFCPropertySheet::AddTreeCategory](#addtreecategory) método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al nuevo nodo en el control de árbol.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para agregar un nuevo nodo, que también se conoce como una categoría, para el control de árbol. Para agregar un nodo, cree una `CMFCPropertySheet` objeto, llame a la [CMFCPropertySheet:: Setlook](#setlook) método con el `look` parámetro establecido en `CMFCPropertySheet::PropSheetLook_Tree`y, a continuación, use este método para agregar el nodo.  
  
 Usa el valor devuelto de este método en las llamadas subsiguientes a [CMFCPropertySheet::AddPageToTree](#addpagetotree) y [CMFCPropertySheet::AddTreeCategory](#addtreecategory).  
  
##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet  
 Construye un objeto `CMFCPropertySheet`.  
  
```  
CMFCPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszCaption`  
 Una cadena que contiene el título de la hoja de propiedades. No puede ser `NULL`.  
  
 [in] `nIDCaption`  
 Un identificador de recurso que contiene el título de la hoja de propiedades.  
  
 [in] `pParentWnd`  
 Puntero a la ventana primaria de la hoja de propiedades, o `NULL` si la ventana primaria es la ventana principal de la aplicación. El valor predeterminado es `NULL`.  
  
 [in] `iSelectPage`  
 Índice de base cero de la página de propiedades principales. El valor predeterminado es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea los parámetros para la [CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) constructor.  
  
##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader  
 Reserva espacio en la parte superior de cada página para dibujar un encabezado personalizado.  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHeaderHeight`  
 El alto del encabezado, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Para usar el valor de la `nHeaderHeight` parámetro para dibujar un encabezado personalizado, invalide el [CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader) método.  
  
##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight  
 Recupera el alto del encabezado actual.  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del encabezado, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a la [CMFCPropertySheet::EnablePageHeader](#enablepageheader) método antes de llamar a este método.  
  
##  <a name="getlook"></a>  CMFCPropertySheet::GetLook  
 Recupera un valor de enumeración que especifica el aspecto de la hoja de propiedades actual.  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores de enumeración que especifica el aspecto de la hoja de propiedades. Para obtener una lista de valores posibles, vea la tabla de enumeración en la sección Comentarios de [CMFCPropertySheet:: Setlook](#setlook).  
  
##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth  
 Obtiene el ancho de la barra de navegación.  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ancho de la barra de navegación, en píxeles.  
  
##  <a name="gettab"></a>  CMFCPropertySheet::GetTab  
 Recupera el objeto de control de la pestaña interna que admite el control de la hoja de propiedades actual.  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de control interno (ficha).  
  
### <a name="remarks"></a>Comentarios  
 Puede establecer una hoja de propiedades para que aparezca en los estilos diferentes, por ejemplo, un control de árbol, una lista de botones de navegación o un conjunto de páginas con pestañas.  
  
 Antes de llamar a este método, llame a la [CMFCPropertySheet:: Setlook](#setlook) método para establecer la apariencia del control de hoja de propiedades. A continuación, llame a la [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) método para inicializar el objeto de control de pestaña interna. Utilice este método para recuperar el objeto de control de pestaña y, a continuación, usar ese objeto para trabajar con las pestañas en la hoja de propiedades.  
  
 Este método valida en modo de depuración, si el control de la hoja de propiedades no está configurado para aparecer en el estilo de Microsoft OneNote.  
  
##  <a name="initnavigationcontrol"></a>  CMFCPropertySheet::InitNavigationControl  
 Inicializa el aspecto del control de la hoja de propiedades actual.  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de control de la hoja de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Puede aparecer un control de la hoja de propiedades en diferentes formatos, como un conjunto de páginas con pestañas, un control de árbol o una lista de botones de navegación. Use la [CMFCPropertySheet:: Setlook](#setlook) método para especificar la apariencia del control de hoja de propiedades.  
  
##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage  
 Lo llama el marco de trabajo cuando se ha habilitado una página de propiedades.  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPage`  
 Puntero a un objeto de página de propiedad que representa la página de la propiedad enabled.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método garantiza que la página de la propiedad enabled se desplaza en la vista. Si el estilo de la hoja de propiedades actual contiene un panel de Microsoft Outlook, este método establece el botón correspondiente de Outlook en el estado de activación.  
  
##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader  
 Lo llama el marco de trabajo para dibujar el encabezado de una página de propiedades personalizadas.  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `nPage`  
 El número de página de la propiedad de base cero.  
  
 [in] `rectHeader`  
 Un rectángulo delimitador que especifica dónde debe dibujar el encabezado.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método no hace nada. Si invalida este método, llame a la [CMFCPropertySheet::EnablePageHeader](#enablepageheader) método antes de que el marco de trabajo llama a este método.  
  
##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage  
 Lo llama el marco de trabajo para quitar una página de propiedades de un control de árbol.  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPage`  
 Puntero a un objeto de página de propiedad que representa la página de propiedades para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory  
 Quita un nodo del control de árbol.  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCategory`  
 Puntero a una categoría (nodo) que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Use este método para quitar un nodo, que también se conoce como una categoría de un control de árbol. Use la [CMFCPropertySheet::AddTreeCategory](#addtreecategory) método para agregar un nodo a un control de árbol.  
  
##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage  
 Quita una página de propiedades de la hoja de propiedades.  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPage`  
 Puntero al objeto de la página de propiedad que representa la página de propiedades para quitar. No puede ser `NULL`.  
  
 [in] `nPage`  
 Índice de base cero de la página para quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita la página de propiedades especificada y destruye la ventana asociada. La página de propiedades del objeto que la `pPage` parámetro especifica que no se destruye hasta que el [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) ventana está cerrada.  
  
##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList  
 Especifica la lista de imágenes que se usan en el control de navegación del panel de Outlook.  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiImageListResID`  
 El identificador de recurso de una lista de imágenes.  
  
 [in] `cx`  
 El ancho, en píxeles, de los iconos en la lista de imágenes.  
  
 [in] `clrTransparent`  
 El color de imagen transparente. Las partes de la imagen que son de este color será transparentes. El valor predeterminado es el color fucsia, RGB(255,0,255).  
  
 [in] `hIcons`  
 Identificador de una lista de imágenes existente.  
  
### <a name="return-value"></a>Valor devuelto  
 En el primer método de sobrecarga sintaxis, `TRUE` si este método es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si la hoja de propiedades se encuentra en el estilo de Microsoft Outlook, el marco de trabajo muestra una lista de botones de navegación, denominado el control de panel de Outlook, a la izquierda de la hoja de propiedades. Utilice este método para establecer la lista de imágenes que va a usar el control de panel de Outlook.  
  
 Para obtener más información acerca de los métodos que admite este método, consulte [CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) y [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Para obtener más información acerca de cómo establecer el estilo de una hoja de propiedades, vea [CMFCPropertySheet:: Setlook](#setlook).  
  
##  <a name="setlook"></a>  CMFCPropertySheet:: Setlook  
 Especifica el aspecto de la hoja de propiedades.  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `look`  
 Uno de los valores de enumeración que especifica el aspecto de la hoja de propiedades. El estilo predeterminado para una hoja de propiedades es `CMFCPropertySheet::PropSheetLook_Tabs`. Para obtener más información, vea la tabla en la sección Comentarios de este tema.  
  
 [in] `nNavControlWidth`  
 El ancho del control de navegación, en píxeles. El valor predeterminado es 100.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar una hoja de propiedades en un estilo distinto del predeterminado, llame a este método antes de crear la ventana de la hoja de propiedades.  
  
 En la tabla siguiente se enumera los valores de enumeración que se pueden especificar en el `look` parámetro.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Valor predeterminado) Muestra una pestaña para cada página de propiedades. Las pestañas se muestran en la parte superior de la hoja de propiedades y se apilan si hay más fichas que caben en una sola fila.|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Muestra una lista de botones de navegación, en el estilo de la barra de Outlook de Microsoft, en el lado izquierdo de la hoja de propiedades. Cada botón en la lista corresponde a una página de propiedades. El marco de trabajo muestra las flechas de desplazamiento si hay varios botones que caben en el área visible de la lista.|  
|`CMFCPropertySheet::PropSheetLook_Tree`|Muestra un control de árbol en el lado izquierdo de la hoja de propiedades. Cada nodo primario o secundario del control de árbol corresponde a una página de propiedades. El marco de trabajo muestra las flechas de desplazamiento si no hay más nodos de los que caben en el área visible del control de árbol.|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Muestra una ficha, en el estilo de Microsoft OneNote, para cada página de propiedades. El marco de trabajo muestra las fichas en la parte superior de la hoja de propiedades y las flechas de desplazamiento si hay más fichas que quepan en una sola fila.|  
|`CMFCPropertySheet::PropSheetLook_List`|Muestra una lista en el lado izquierdo de la hoja de propiedades. Cada elemento de la lista corresponde a una página de propiedades. El marco de trabajo muestra las flechas de desplazamiento si hay más elementos de lista que caben en el área visible de la lista.|  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)
