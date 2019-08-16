---
title: Clase CMFCPropertySheet
ms.date: 11/19/2018
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
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505047"
---
# <a name="cmfcpropertysheet-class"></a>Clase CMFCPropertySheet

La clase `CMFCPropertySheet` admite una hoja de propiedades donde cada página de propiedades se indica mediante una pestaña de página, un botón de barra de herramientas, un nodo del control de árbol o un elemento de lista.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Construye un objeto `CMFCPropertySheet`.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Agrega una página a la hoja de propiedades.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Agrega una nueva página de propiedades al control de árbol.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Agrega un nuevo nodo al control de árbol.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Reserva espacio en la parte superior de cada página para dibujar un encabezado personalizado.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Recupera el alto del encabezado actual.|
|[CMFCPropertySheet::GetLook](#getlook)|Recupera un valor de enumeración que especifica el aspecto de la hoja de propiedades actual.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Recupera el ancho de la barra de navegación, en píxeles.|
|[CMFCPropertySheet::GetTab](#gettab)|Recupera el objeto de control de la pestaña interna que admite el control de la hoja de propiedades actual.|
|`CMFCPropertySheet::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializa el aspecto del control de la hoja de propiedades actual.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Lo llama el marco de trabajo cuando se ha habilitado una página de propiedades.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Lo llama el marco de trabajo para dibujar un encabezado de la página de propiedades personalizada.|
|`CMFCPropertySheet::OnInitDialog`|Controla el mensaje [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Invalida [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)).|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Lo llama el marco de trabajo para quitar una página de propiedades de un control de árbol.|
|`CMFCPropertySheet::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Invalida `CPropertySheet::PreTranslateMessage`).|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Quita un nodo del control de árbol.|
|[CMFCPropertySheet::RemovePage](#removepage)|Quita una página de propiedades de la hoja de propiedades.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Especifica la lista de imágenes que se usan en el control de navegación del panel de Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Especifica el aspecto de la hoja de propiedades.|

## <a name="remarks"></a>Comentarios

La clase `CMFCPropertySheet` representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña. La clase `CMFCPropertySheet` puede mostrar una página de propiedades de varias formas.

Realice los pasos siguientes para usar la clase `CMFCPropertySheet` en la aplicación:

1. Derive una clase de la clase `CMFCPropertySheet` y llámela, por ejemplo, CMyPropertySheet.

1. Construya un objeto [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) para cada página de propiedades.

1. Llame al método [CMFCPropertySheet:: SetLook](#setlook) en el constructor CMyPropertySheet. Un parámetro de ese método especifica que las páginas de propiedades se mostrarán como pestañas a lo largo de la parte superior o izquierda de la hoja de propiedades, como pestañas en el estilo de una hoja de propiedades de Microsoft OneNote, como botones en un control de barra de herramientas de Microsoft Outlook, como nodos en un control de árbol o como una lista de elementos en el lado izquierdo de la hoja de propiedades.

1. Si crea una hoja de propiedades en el estilo de una barra de herramientas de Microsoft Outlook, llame al método [CMFCPropertySheet:: SetIconsList](#seticonslist) para asociar una lista de imágenes junto con las páginas de propiedades.

1. Llame al método [CMFCPropertySheet:: AddPage](#addpage) para cada página de propiedades.

1. Cree un control `CMFCPropertySheet` y llame a su método `DoModal`.

## <a name="illustrations"></a>Ilustraciones

La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de una barra de herramientas incrustada de Microsoft Outlook. La barra de herramientas de Outlook aparece en el lado izquierdo de la hoja de propiedades.

![Controles de color de CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Controles de color de CMFCPropertySheet")

En la ilustración siguiente se muestra una hoja de propiedades que contiene un objeto de la [clase cmfcpropertygridctrl (](../../mfc/reference/cmfcpropertygridctrl-class.md) . Ese objeto es una hoja de propiedades del estilo de una hoja de propiedades de controles comunes estándar.

![Lista de CMFCPropertySheet y controles de propiedad](../../mfc/reference/media/cmfcpropertysheet_list.png "Lista de CMFCPropertySheet y controles de propiedad")

La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de un control de árbol.

![Árbol de propiedades](../../mfc/reference/media/proptree.png "Árbol de propiedades")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertysheet. h

##  <a name="addpage"></a>  CMFCPropertySheet::AddPage

Agrega una página a la hoja de propiedades.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
de Puntero a un objeto de página. Este parámetro no puede ser NULL.

### <a name="remarks"></a>Comentarios

Este método agrega la página de propiedades especificada como la pestaña situada más a la derecha en la hoja de propiedades. Por lo tanto, use este método para agregar páginas en orden de izquierda a derecha.

Si la hoja de propiedades está en el estilo de Microsoft Outlook, el marco de trabajo muestra una lista de botones de navegación a la izquierda de la hoja de propiedades. Después de que este método agrega una página de propiedades, agrega el botón correspondiente a la lista. Para mostrar una página de propiedades, haga clic en el botón correspondiente. Para obtener más información sobre los estilos de las hojas de propiedades, vea [CMFCPropertySheet:: SetLook](#setlook).

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

*pCategory*<br/>
de Puntero a un nodo de árbol primario o NULL para asociar la página especificada con el nodo de nivel superior. Llame al método [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) para obtener este puntero.

*pPage*<br/>
de Puntero a un objeto de página de propiedades.

*nIconNum*<br/>
de Índice de base cero de un icono o-1 si no se usa ningún icono. El icono se muestra junto a la página de propiedades del control de árbol cuando la página no está seleccionada. El valor predeterminado es -1.

*nSelIconNum*<br/>
de Índice de base cero de un icono o-1 si no se usa ningún icono. Cuando se selecciona la página, se muestra el icono junto a la página de propiedades del control de árbol. El valor predeterminado es -1.

### <a name="remarks"></a>Comentarios

Este método agrega una página de propiedades como hoja de un control de árbol. Para agregar una página de propiedades, cree `CMFCPropertySheet` un objeto, llame al método [CMFCPropertySheet:: SetLook](#setlook) con el parámetro *look* establecido `CMFCPropertySheet::PropSheetLook_Tree`en y, a continuación, use este método para agregar la página de propiedades.

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

*lpszLabel*<br/>
de Nombre del nodo.

*nIconNum*<br/>
de Índice de base cero de un icono o-1 si no se usa ningún icono. El icono se muestra junto a la página de propiedades del control de árbol cuando la página no está seleccionada. El valor predeterminado es -1.

*nSelectedIconNum*<br/>
de Índice de base cero de un icono o-1 si no se usa ningún icono. Cuando se selecciona la página, se muestra el icono junto a la página de propiedades del control de árbol. El valor predeterminado es -1.

*pParentCategory*<br/>
de Puntero a un nodo de árbol primario o NULL para asociar la página especificada con el nodo de nivel superior. Establezca este parámetro con el método [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo nodo en el control de árbol.

### <a name="remarks"></a>Comentarios

Utilice este método para agregar un nuevo nodo, al que también se hace referencia como categoría, al control de árbol. Para agregar un nodo, cree un `CMFCPropertySheet` objeto, llame al método [CMFCPropertySheet:: SetLook](#setlook) con el parámetro *look* establecido en `CMFCPropertySheet::PropSheetLook_Tree`y, a continuación, use este método para agregar el nodo.

Use el valor devuelto de este método en las llamadas posteriores a [CMFCPropertySheet:: AddPageToTree](#addpagetotree) y [CMFCPropertySheet:: AddTreeCategory](#addtreecategory).

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

*pszCaption*<br/>
de Cadena que contiene el título de la hoja de propiedades. No puede ser nulo.

*nIDCaption*<br/>
de IDENTIFICADOR de recurso que contiene el título de la hoja de propiedades.

*pParentWnd*<br/>
de Puntero a la ventana primaria de la hoja de propiedades, o NULL si la ventana primaria es la ventana principal de la aplicación. El valor predeterminado es NULL.

*iSelectPage*<br/>
de Índice de base cero de la página de propiedades superior. El valor predeterminado es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea los parámetros del constructor [CPropertySheet:: CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) .

##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader

Reserva espacio en la parte superior de cada página para dibujar un encabezado personalizado.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parámetros

*nHeaderHeight*<br/>
de Alto del encabezado, en píxeles.

### <a name="remarks"></a>Comentarios

Para usar el valor del parámetro *nHeaderHeight* para dibujar un encabezado personalizado, invalide el método [CMFCPropertySheet:: OnDrawPageHeader](#ondrawpageheader) .

##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight

Recupera el alto del encabezado actual.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Valor devuelto

Alto del encabezado, en píxeles.

### <a name="remarks"></a>Comentarios

Llame al método [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) antes de llamar a este método.

##  <a name="getlook"></a>  CMFCPropertySheet::GetLook

Recupera un valor de enumeración que especifica el aspecto de la hoja de propiedades actual.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Valor devuelto

Uno de los valores de enumeración que especifica la apariencia de la hoja de propiedades. Para obtener una lista de los valores posibles, vea la tabla de enumeración en la sección Comentarios de [CMFCPropertySheet:: SetLook](#setlook).

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

Objeto de control de pestaña interno.

### <a name="remarks"></a>Comentarios

Puede establecer una hoja de propiedades para que aparezca en distintos estilos, como un control de árbol, una lista de botones de navegación o un conjunto de páginas con pestañas.

Antes de llamar a este método, llame al método [CMFCPropertySheet:: SetLook](#setlook) para establecer la apariencia del control de la hoja de propiedades. A continuación, llame al método [CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol) para inicializar el objeto de control de pestaña interno. Utilice este método para recuperar el objeto de control de pestaña y, a continuación, use ese objeto para trabajar con las pestañas de la hoja de propiedades.

Este método se valida en modo de depuración si el control de la hoja de propiedades no está establecido para aparecer en el estilo de Microsoft OneNote.

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet:: InitNavigationControl

Inicializa el aspecto del control de la hoja de propiedades actual.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana del control de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

Un control de hoja de propiedades puede aparecer en varios formatos diferentes, como un conjunto de páginas con pestañas, un control de árbol o una lista de botones de navegación. Use el método [CMFCPropertySheet:: SetLook](#setlook) para especificar la apariencia del control de la hoja de propiedades.

##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage

Lo llama el marco de trabajo cuando se ha habilitado una página de propiedades.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
de Puntero a un objeto de página de propiedades que representa la página de propiedades habilitada.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método garantiza que la página de propiedades habilitada se desplaza a la vista. Si el estilo de la hoja de propiedades actual contiene un panel de Microsoft Outlook, este método establece el correspondiente botón de Outlook en el estado activado.

##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader

Lo llama el marco de trabajo para dibujar el encabezado de una página de propiedades personalizada.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo.

*nPage*<br/>
de Número de la página de propiedades de base cero.

*rectHeader*<br/>
de Rectángulo delimitador que especifica dónde se debe dibujar el encabezado.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada. Si invalida este método, llame al método [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) antes de que el marco de trabajo llame a este método.

##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage

Lo llama el marco de trabajo para quitar una página de propiedades de un control de árbol.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
de Puntero a un objeto de página de propiedades que representa la página de propiedades que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory

Quita un nodo del control de árbol.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parámetros

*pCategory*<br/>
de Puntero a una categoría (nodo) que se va a quitar.

### <a name="remarks"></a>Comentarios

Utilice este método para quitar un nodo, que también se conoce como una categoría, de un control de árbol. Use el método [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) para agregar un nodo a un control de árbol.

##  <a name="removepage"></a>CMFCPropertySheet:: RemovePage

Quita una página de propiedades de la hoja de propiedades.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
de Puntero al objeto de página de propiedades que representa la página de propiedades que se va a quitar. No puede ser nulo.

*nPage*<br/>
de Índice de base cero de la página que se va a quitar.

### <a name="remarks"></a>Comentarios

Este método quita la página de propiedades especificada y destruye su ventana asociada. El objeto de página de propiedades que especifica el parámetro *pPage* no se destruye hasta que se cierra la ventana [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) .

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

*uiImageListResID*<br/>
de El identificador de recurso de una lista de imágenes.

*cx*<br/>
de Ancho, en píxeles, de los iconos de la lista de imágenes.

*clrTransparent*<br/>
de Color de imagen transparente. Las partes de la imagen que son este color serán transparentes. El valor predeterminado es el color magenta, RGB (255, 0255).

*hIcons*<br/>
de Identificador de una lista de imágenes existente.

### <a name="return-value"></a>Valor devuelto

En la primera sintaxis de sobrecarga del método, es TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si la hoja de propiedades está en el estilo de Microsoft Outlook, el marco de trabajo muestra una lista de botones de navegación, denominada control del panel de Outlook, a la izquierda de la hoja de propiedades. Use este método para establecer la lista de imágenes que va a usar el control de panel de Outlook.

Para obtener más información sobre los métodos que admiten este método, vea [CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) y [CImageList:: Add](../../mfc/reference/cimagelist-class.md#add). Para obtener más información sobre cómo establecer el estilo de una hoja de propiedades, vea [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="setlook"></a>CMFCPropertySheet:: SetLook

Especifica el aspecto de la hoja de propiedades.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parámetros

*look*<br/>
de Uno de los valores de enumeración que especifica la apariencia de la hoja de propiedades. El estilo predeterminado para una hoja de propiedades `CMFCPropertySheet::PropSheetLook_Tabs`es. Para obtener más información, vea la tabla en la sección Comentarios de este tema.

*nNavControlWidth*<br/>
de Ancho del control de navegación, en píxeles. El valor predeterminado es 100.

### <a name="remarks"></a>Comentarios

Para mostrar una hoja de propiedades en un estilo distinto del predeterminado, llame a este método antes de crear la ventana de la hoja de propiedades.

En la tabla siguiente se enumeran los valores de enumeración que se pueden especificar en el parámetro *look* .

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|Predeterminada Muestra una pestaña para cada página de propiedades. Las pestañas se muestran en la parte superior de la hoja de propiedades y se apilan si hay más pestañas de las que caben en una sola fila.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Muestra una lista de botones de navegación, en el estilo de la barra de Microsoft Outlook, en el lado izquierdo de la hoja de propiedades. Cada botón de la lista corresponde a una página de propiedades. El marco de trabajo muestra flechas de desplazamiento si hay más botones de los que caben en el área visible de la lista.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Muestra un control de árbol en el lado izquierdo de la hoja de propiedades. Cada nodo primario o secundario del control de árbol corresponde a una página de propiedades. El marco de trabajo muestra flechas de desplazamiento si hay más nodos de los que caben en el área visible del control de árbol.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Muestra una pestaña, en el estilo de Microsoft OneNote, para cada página de propiedades. El marco de trabajo muestra las pestañas en la parte superior de la hoja de propiedades y las flechas de desplazamiento si hay más pestañas de las que caben en una sola fila.|
|`CMFCPropertySheet::PropSheetLook_List`|Muestra una lista en el lado izquierdo de la hoja de propiedades. Cada elemento de la lista corresponde a una página de propiedades. El marco de trabajo muestra flechas de desplazamiento si hay más elementos de lista de los que caben en el área visible de la lista.|

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage (clase)](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)
