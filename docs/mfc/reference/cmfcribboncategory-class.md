---
title: CMFCRibbonCategory (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCategory [MFC], CMFCRibbonCategory
- CMFCRibbonCategory [MFC], AddHidden
- CMFCRibbonCategory [MFC], AddPanel
- CMFCRibbonCategory [MFC], CopyFrom
- CMFCRibbonCategory [MFC], FindByData
- CMFCRibbonCategory [MFC], FindByID
- CMFCRibbonCategory [MFC], FindPanelWithElem
- CMFCRibbonCategory [MFC], GetContextID
- CMFCRibbonCategory [MFC], GetData
- CMFCRibbonCategory [MFC], GetDroppedDown
- CMFCRibbonCategory [MFC], GetElements
- CMFCRibbonCategory [MFC], GetElementsByID
- CMFCRibbonCategory [MFC], GetFirstVisibleElement
- CMFCRibbonCategory [MFC], GetFocused
- CMFCRibbonCategory [MFC], GetHighlighted
- CMFCRibbonCategory [MFC], GetImageCount
- CMFCRibbonCategory [MFC], GetImageSize
- CMFCRibbonCategory [MFC], GetItemIDsList
- CMFCRibbonCategory [MFC], GetLastVisibleElement
- CMFCRibbonCategory [MFC], GetLargeImages
- CMFCRibbonCategory [MFC], GetMaxHeight
- CMFCRibbonCategory [MFC], GetName
- CMFCRibbonCategory [MFC], GetPanel
- CMFCRibbonCategory [MFC], GetPanelCount
- CMFCRibbonCategory [MFC], GetPanelFromPoint
- CMFCRibbonCategory [MFC], GetPanelIndex
- CMFCRibbonCategory [MFC], GetParentButton
- CMFCRibbonCategory [MFC], GetParentMenuBar
- CMFCRibbonCategory [MFC], GetParentRibbonBar
- CMFCRibbonCategory [MFC], GetRect
- CMFCRibbonCategory [MFC], GetSmallImages
- CMFCRibbonCategory [MFC], GetTabColor
- CMFCRibbonCategory [MFC], GetTabRect
- CMFCRibbonCategory [MFC], GetTextTopLine
- CMFCRibbonCategory [MFC], GetVisibleElements
- CMFCRibbonCategory [MFC], HighlightPanel
- CMFCRibbonCategory [MFC], HitTest
- CMFCRibbonCategory [MFC], HitTestEx
- CMFCRibbonCategory [MFC], HitTestScrollButtons
- CMFCRibbonCategory [MFC], IsActive
- CMFCRibbonCategory [MFC], IsVisible
- CMFCRibbonCategory [MFC], IsWindows7Look
- CMFCRibbonCategory [MFC], NotifyControlCommand
- CMFCRibbonCategory [MFC], OnCancelMode
- CMFCRibbonCategory [MFC], OnDraw
- CMFCRibbonCategory [MFC], OnDrawImage
- CMFCRibbonCategory [MFC], OnDrawMenuBorder
- CMFCRibbonCategory [MFC], OnKey
- CMFCRibbonCategory [MFC], OnLButtonDown
- CMFCRibbonCategory [MFC], OnLButtonUp
- CMFCRibbonCategory [MFC], OnMouseMove
- CMFCRibbonCategory [MFC], OnRTLChanged
- CMFCRibbonCategory [MFC], OnScrollHorz
- CMFCRibbonCategory [MFC], OnUpdateCmdUI
- CMFCRibbonCategory [MFC], RecalcLayout
- CMFCRibbonCategory [MFC], RemovePanel
- CMFCRibbonCategory [MFC], ReposPanels
- CMFCRibbonCategory [MFC], SetCollapseOrder
- CMFCRibbonCategory [MFC], SetData
- CMFCRibbonCategory [MFC], SetKeys
- CMFCRibbonCategory [MFC], SetName
- CMFCRibbonCategory [MFC], SetTabColor
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73cf6b78475ca438c39e52263c4e91b10de60f8c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020425"
---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory (clase)
El `CMFCRibbonCategory` clase implementa una pestaña de cinta que contiene un grupo de [paneles de cinta de opciones](../../mfc/reference/cmfcribbonpanel-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](#addhidden)|Agrega un elemento oculto a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::AddPanel](#addpanel)|Agrega un nuevo panel a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||  
|[CMFCRibbonCategory::FindByData](#findbydata)||  
|[CMFCRibbonCategory::FindByID](#findbyid)||  
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||  
|[CMFCRibbonCategory::GetContextID](#getcontextid)|Devuelve el identificador de contexto de la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetData](#getdata)|Devuelve los datos definidos por el usuario que está asociados a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonCategory::GetElements](#getelements)||  
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|Obtenga un primer elemento visible que pertenecen a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetFocused](#getfocused)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|Devuelve un elemento resaltado.|  
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||  
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||  
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|Obtener un último elemento visible que pertenecen a la categoría de cinta de opciones|  
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|Devuelve una referencia a la lista de imágenes grandes que usa la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||  
|[CMFCRibbonCategory::GetName](#getname)||  
|[CMFCRibbonCategory::GetPanel](#getpanel)|Devuelve un puntero al panel de cinta de opciones que se encuentra en el índice especificado.|  
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|Devuelve el número de paneles de cinta en la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||  
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|Devuelve el índice del panel de la cinta especificada.|  
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||  
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||  
|[CMFCRibbonCategory::GetRect](#getrect)||  
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|Devuelve una referencia a la lista de imágenes pequeñas que usa la categoría.|  
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|Devuelve el color actual de la pestaña de categoría de cinta de opciones.|  
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||  
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||  
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|Obtener todos los elementos visibles que pertenecen a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||  
|[CMFCRibbonCategory::HitTest](#hittest)||  
|[CMFCRibbonCategory::HitTestEx](#hittestex)||  
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||  
|[CMFCRibbonCategory::IsActive](#isactive)||  
|[CMFCRibbonCategory::IsVisible](#isvisible)|Determina si la categoría de cinta de opciones está visible.|  
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|Indica si la cinta de opciones del elemento primario tiene Windows 7 apariencia (botón de aplicación rectangular pequeño)|  
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||  
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||  
|[CMFCRibbonCategory::OnDraw](#ondraw)||  
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||  
|[CMFCRibbonCategory::OnKey](#onkey)|Lo llama el marco cuando el usuario presiona un botón de teclado.|  
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||  
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||  
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||  
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||  
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||  
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||  
|[CMFCRibbonCategory::RemovePanel](#removepanel)||  
|[CMFCRibbonCategory::ReposPanels](#repospanels)||  
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|Define el orden de contracción de los paneles de cinta de opciones que se encuentran en la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::SetData](#setdata)|Almacena los datos definidos por el usuario en la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::SetKeys](#setkeys)|Keytip se asigna a la categoría de cinta de opciones.|  
|[CMFCRibbonCategory::SetName](#setname)||  
|[CMFCRibbonCategory:: Settabcolor](#settabcolor)|Establece el color de la categoría de cinta de opciones.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, se crea una categoría de cinta indirectamente mediante una llamada a [CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory), que devuelve un puntero a la categoría de cinta recién creado. Agregar paneles a la categoría mediante una llamada a [CMFCRibbonCategory::AddPanel](#addpanel).  
  
 La `CMFCRibbonTab` clase dibuja las categorías de la cinta de opciones. Se deriva [CMFCRibbonBaseElement (clase)](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 En el ejemplo siguiente se muestra cómo crear una categoría de cinta de opciones y agregar un panel a él.  
  
```cpp
// Create a new ribbon category and get a pointer to it`  
CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory
    (_T("&Write"),           // Category name
    IDB_WRITE,               // Category small images (16 x 16)
    IDB_WRITE_LARGE);        // Category large images (32 x 32)

// Add a panel to the new category
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"),                // Panel name
    m_PanelIcons.ExtractIcon (0));  // Panel icon
```
  
 El siguiente diagrama muestra una ilustración de la categoría principal de la aplicación de ejemplo RibbonApp.  
  
 ![Imagen de CMFCRibbonCategory](../../mfc/reference/media/cmfcribboncategory.png "cmfcribboncategory")  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCRibbonCategory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncategory.h  
  
##  <a name="addhidden"></a>  CMFCRibbonCategory::AddHidden  
 Agrega el elemento especificado de la cinta de opciones a la matriz de elementos de la cinta de opciones que se muestran en el cuadro de diálogo de personalización.  
  
```  
void AddHidden(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
*pElem*<br/>
[in] Puntero a un elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la cinta de opciones en el cuadro de diálogo de personalización son los comandos que se pueden agregar a la barra de herramientas de acceso rápido.  
  
##  <a name="addpanel"></a>  CMFCRibbonCategory::AddPanel  
 Crea un panel de cinta de opciones para la categoría de cinta de opciones.  
  
```  
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,  
    HICON hIcon = 0,  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszPanelName*<br/>
[in] Puntero al nombre del nuevo panel de cinta de opciones.  
  
*hIcon*<br/>
[in] Handle para el icono predeterminado para el nuevo panel de cinta de opciones.  
  
*pRTI*<br/>
[in] Puntero a la información de clase en tiempo de ejecución para un panel de cinta de opciones personalizada.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero en el panel de la cinta de nuevo si el método se realizó correctamente; en caso contrario, es NULL si no se creó el panel.  
  
### <a name="remarks"></a>Comentarios  
 Si desea crear un panel de cinta de opciones personalizada, debe especificar su información de clase en tiempo de ejecución en *pRTI*. La clase del panel de cinta de opciones personalizada debe derivarse de la `CMFCRibbonPanel` clase.  
  
 El icono predeterminado para el panel de la cinta se muestra cuando no hay suficiente espacio para mostrar los elementos de la cinta de opciones.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el `AddPanel` método en el `CMFCRibbonCategory` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp#10](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]  
  
##  <a name="cmfcribboncategory"></a>  CMFCRibbonCategory::CMFCRibbonCategory  
 Crea e inicializa un [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objeto.  
  
```  
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,  
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32));
```  
  
### <a name="parameters"></a>Parámetros  
*pParenrRibbonBar*<br/>
[in] Puntero a la barra de cinta de opciones de elemento primario de la categoría de cinta de opciones.  
  
*lpszName*<br/>
[in] Nombre de la categoría de cinta de opciones.  
  
*uiSmallImagesResID*<br/>
[in] Identificador de recurso de la lista de imágenes para las imágenes pequeñas que se usan los elementos de la cinta de opciones de la categoría de cinta de opciones.  
  
*uiLargeImagesResID*<br/>
[in] Identificador de recurso de la lista de imágenes para las imágenes grandes que se usan los elementos de la cinta de opciones de la categoría de cinta de opciones.  
  
*sizeSmallImage*<br/>
[in] Tamaño de imágenes pequeñas para los elementos de la cinta de opciones en la categoría de cinta de opciones de forma predeterminada.  
  
*sizeLargeImage*<br/>
[in] Tamaño de imágenes de gran tamaño para los elementos de la cinta de opciones en la categoría de cinta de opciones de forma predeterminada.  
  
##  <a name="copyfrom"></a>  CMFCRibbonCategory::CopyFrom  
 Copia el estado del elemento especificado [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) actual [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objeto.  
  
```  
virtual void CopyFrom(CMFCRibbonCategory& src);
```  
  
### <a name="parameters"></a>Parámetros  
*src*<br/>
[in] El origen `CMFCRibbonCategory` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findbydata"></a>  CMFCRibbonCategory::FindByData  
 Recupera el elemento de la cinta de opciones asociado con los datos especificados.  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*dwData*<br/>
[in] Los datos asociados con un elemento de la cinta.  
  
*bVisibleOnly*<br/>
[in] TRUE para incluir elementos de la cinta de opciones de acceso rápido en la búsqueda; FALSE para excluir elementos de la cinta de opciones de acceso rápido en la búsqueda.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findbyid"></a>  CMFCRibbonCategory::FindByID  
 Recupera el elemento de la cinta de opciones asociado al identificador de comando especificado.  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*uiCmdID*<br/>
[in] Identificador de comando asociado con un elemento de la cinta de opciones.  
  
*bVisibleOnly*<br/>
[in] TRUE para incluir elementos de la cinta de opciones de acceso rápido en la búsqueda; FALSE para excluir elementos de la cinta de opciones de acceso rápido en la búsqueda.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findpanelwithelem"></a>  CMFCRibbonCategory::FindPanelWithElem  
 Recupera el panel de la cinta que contiene el elemento especificado de la cinta de opciones.  
  
```  
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Parámetros  
*pElement*<br/>
[in] Puntero a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un panel de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcontextid"></a>  CMFCRibbonCategory::GetContextID  
 Recupera el identificador de contexto de la categoría de cinta de opciones.  
  
```  
UINT GetContextID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Id. de contexto de la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El identificador de contexto es 0 si la categoría de cinta de opciones no es una categoría de cinta de opciones de contexto.  
  
##  <a name="getdata"></a>  CMFCRibbonCategory::GetData  
 Recupera los datos definidos por el usuario que está asociados a la categoría de cinta de opciones.  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos definidos por el usuario que está asociados a la categoría de cinta de opciones.  
  
##  <a name="getdroppeddown"></a>  CMFCRibbonCategory::GetDroppedDown  
 Recupera un puntero al elemento de cinta de opciones que tiene actualmente su menú emergente que aparece.  
  
```  
CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getelements"></a>  CMFCRibbonCategory::GetElements  
 Recupera todos los elementos de la cinta de opciones en la categoría de cinta de opciones.  
  
```  
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
*arElements*<br/>
[in, out] Hacer referencia a un [CArray](../../mfc/reference/carray-class.md) de elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de la cinta de opciones que están diseñados para su uso en la barra de herramientas de acceso rápido se incluyen en la matriz.  
  
##  <a name="getelementsbyid"></a>  CMFCRibbonCategory::GetElementsByID  
 Recupera todos los elementos de la cinta de opciones que están asociados con el identificador de comando especificado.  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
*uiCmdID*<br/>
[in] Identificador de comando asociado con un elemento de la cinta de opciones.  
  
*arElements*<br/>
[in, out] Hacer referencia a un [CArray](../../mfc/reference/carray-class.md) de elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de la cinta de opciones que están diseñados para su uso en la barra de herramientas de acceso rápido se incluyen en la matriz.  
  
##  <a name="getfirstvisibleelement"></a>  CMFCRibbonCategory::GetFirstVisibleElement  
 Recupera el primer elemento visible que pertenece a la categoría de cinta de opciones.  
  
```  
CMFCRibbonBaseElement* GetFirstVisibleElement() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al primer elemento visible; puede ser NULL si la categoría no tiene ningún elemento visible.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getfocused"></a>  CMFCRibbonCategory::GetFocused  
 Devuelve un elemento que tiene el foco.  
  
```  
CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento con foco o NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethighlighted"></a>  CMFCRibbonCategory::GetHighlighted  
 Devuelve un elemento resaltado.  
  
```  
CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento resaltado o NULL si no hay elementos se resaltan.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getimagecount"></a>  CMFCRibbonCategory::GetImageCount  
 Recupera el número de imágenes en la lista de imágenes especificado que se encuentra en la categoría de cinta de opciones.  
  
```  
int GetImageCount(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*bIsLargeImage*<br/>
[in] TRUE para que el número de imágenes en la lista de imágenes grandes; Si es FALSE, el número de imágenes en la lista de imágenes pequeñas.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de imágenes en la lista de imágenes especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getimagesize"></a>  CMFCRibbonCategory::GetImageSize  
 Recupera el tamaño de una imagen en la lista de imágenes especificado que se encuentra en la categoría de cinta de opciones.  
  
```  
CSize GetImageSize(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*bIsLargeImage*<br/>
[in] TRUE para el tamaño de imágenes de gran tamaño. Si es FALSE, el tamaño de imágenes pequeñas.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de una imagen en la lista de imágenes especificado.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño que se recupera incluye el factor de escala de imagen global.  
  
##  <a name="getitemidslist"></a>  CMFCRibbonCategory::GetItemIDsList  
 Recupera los identificadores de comando para los elementos de la cinta de opciones que se encuentran en la categoría de cinta de opciones.  
  
```  
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*lstItems*<br/>
[out] La lista de identificadores de comando para los elementos de la cinta de opciones en la categoría de cinta de opciones.  
  
*bHiddenOnly*<br/>
[in] TRUE para excluir elementos de la cinta de opciones se muestran en los paneles de cinta de opciones en la categoría de cinta de opciones; FALSE para incluir todos los elementos de la cinta de opciones en la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getlargeimages"></a>  CMFCRibbonCategory::GetLargeImages  
 Recupera la lista de imágenes de gran tamaño que se encuentran en la categoría de cinta de opciones.  
  
```  
CMFCToolBarImages& GetLargeImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La lista de imágenes grandes que se encuentran en la categoría de cinta de opciones.  
  
##  <a name="getlastvisibleelement"></a>  CMFCRibbonCategory::GetLastVisibleElement  
 Recupera el último elemento visible que pertenece a la categoría de cinta de opciones.  
  
```  
CMFCRibbonBaseElement* GetLastVisibleElement() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al último elemento visible; puede ser NULL si la categoría no tiene ningún elemento visible.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmaxheight"></a>  CMFCRibbonCategory::GetMaxHeight  
 Recupera el alto máximo de los paneles de cinta de opciones que se encuentran en la categoría de cinta de opciones.  
  
```  
int GetMaxHeight(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo para los paneles de cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto máximo de los paneles de cinta de opciones que figuran en la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El valor recuperado incluye el alto de los márgenes superior e inferior de los paneles de cinta de opciones.  
  
##  <a name="getname"></a>  CMFCRibbonCategory::GetName  
 Recupera el nombre de la categoría de cinta de opciones.  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre de la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpanel"></a>  CMFCRibbonCategory::GetPanel  
 Devuelve un puntero al panel de cinta de opciones que se encuentra en el índice especificado.  
  
```  
CMFCRibbonPanel* GetPanel(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
*nIndex*<br/>
[in] Índice de base cero de un panel de cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero en el panel de cinta de opciones que se encuentra en el índice especificado.  
  
### <a name="remarks"></a>Comentarios  
 Se produce una excepción si *nIndex* está fuera del intervalo.  
  
##  <a name="getpanelcount"></a>  CMFCRibbonCategory::GetPanelCount  
 Devuelve el número de paneles de cinta en la categoría de cinta de opciones.  
  
```  
int GetPanelCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles de cinta en la categoría de cinta de opciones.  
  
##  <a name="getpanelfrompoint"></a>  CMFCRibbonCategory::GetPanelFromPoint  
 Recupera un puntero a un panel de la cinta si el punto especificado se encuentra en ella.  
  
```  
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un panel de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Se prueban los paneles de cinta que se encuentran en la categoría de cinta de opciones.  
  
##  <a name="getpanelindex"></a>  CMFCRibbonCategory::GetPanelIndex  
 Recupera el índice de base cero del panel de la cinta especificada.  
  
```  
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*pPanel*<br/>
[in] Puntero a un panel de cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del panel de cinta de opciones especificada si el método se realizó correctamente; en caso contrario,-1.  
  
### <a name="remarks"></a>Comentarios  
 Se buscan en paneles de cinta que se encuentran en la categoría de cinta de opciones.  
  
##  <a name="getparentbutton"></a>  CMFCRibbonCategory::GetParentButton  
 Recupera el elemento de cinta de opciones de elemento primario de la categoría de cinta de opciones.  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al elemento primario de la cinta, o NULL si no hay ningún elemento primario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getparentmenubar"></a>  CMFCRibbonCategory::GetParentMenuBar  
 Devuelve un puntero a la barra de menús principal de la `CMFCRibbonCategory` objeto.  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el contenido de la `m_pParentMenuBar` protegido miembro.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getparentribbonbar"></a>  CMFCRibbonCategory::GetParentRibbonBar  
 Recupera la barra de cinta primario para la categoría de cinta de opciones.  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la barra de cinta primario para la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrect"></a>  CMFCRibbonCategory::GetRect  
 Recupera el rectángulo de presentación para la categoría de cinta de opciones.  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo de presentación para la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo de presentación para la categoría de cinta de opciones no incluye la pestaña de categoría.  
  
##  <a name="getsmallimages"></a>  CMFCRibbonCategory::GetSmallImages  
 Recupera la lista de imágenes pequeñas que se encuentran en la categoría de cinta de opciones.  
  
```  
CMFCToolBarImages& GetSmallImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La lista de imágenes pequeñas que se encuentran en la categoría de cinta de opciones.  
  
##  <a name="gettabcolor"></a>  CMFCRibbonCategory::GetTabColor  
 Devuelve el color actual de la pestaña de categoría de cinta de opciones.  
  
```  
AFX_RibbonCategoryColor GetTabColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color actual de la pestaña de categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto puede ser uno de los valores enumerados siguientes:  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="gettabrect"></a>  CMFCRibbonCategory::GetTabRect  
 Recupera el rectángulo de presentación de la pestaña de categoría de cinta de opciones.  
  
```  
CRect GetTabRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo de presentación de la pestaña de categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettexttopline"></a>  CMFCRibbonCategory::GetTextTopLine  
 Recupera la ubicación vertical del texto en los botones de cinta de opciones en la categoría de cinta de opciones que se muestran imágenes de gran tamaño.  
  
```  
int GetTextTopLine() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ubicación vertical del texto, en píxeles, en los botones de la cinta de opciones que se muestran imágenes de gran tamaño.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getvisibleelements"></a>  CMFCRibbonCategory::GetVisibleElements  
 Recupera todos los elementos visibles que pertenecen a la categoría de cinta de opciones.  
  
```  
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,  
    CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 *arElements*  
 Matriz de todos los elementos visibles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="highlightpanel"></a>  CMFCRibbonCategory::HighlightPanel  
 Resalta el panel de la cinta especificada.  
  
```  
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
*pHLPanel*<br/>
[in] Puntero al panel de cinta de opciones para resaltar.  
  
*punto*<br/>
[in] Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al panel de cinta de opciones resaltado anteriormente; en caso contrario, es NULL si ningún panel de la cinta se resalta cuando se invoca este método.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre cómo resaltar un panel de cinta de opciones, consulte [CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight).  
  
##  <a name="hittest"></a>  CMFCRibbonCategory::HitTest  
 Recupera un puntero a un elemento de la cinta si el punto especificado se encuentra en ella.  
  
```  
CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckPanelCaption = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero del mouse, en relación con la esquina superior izquierda de la ventana.  
  
*bCheckPanelCaption*<br/>
[in] TRUE para probar el título del panel de cinta de opciones; FALSE para excluir el título del panel de cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Se comprueban solo los elementos de cinta de opciones que figuran en la categoría de cinta de opciones.  
  
##  <a name="hittestex"></a>  CMFCRibbonCategory::HitTestEx  
 Recupera el índice de base cero de un elemento de la cinta si el punto especificado se encuentra en ella.  
  
```  
int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero del mouse, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de un elemento de la cinta si el método se realizó correctamente; en caso contrario,-1.  
  
### <a name="remarks"></a>Comentarios  
 Se comprueban solo los elementos de cinta de opciones que figuran en la categoría de cinta de opciones.  
  
##  <a name="hittestscrollbuttons"></a>  CMFCRibbonCategory::HitTestScrollButtons  
 Si se encuentra un punto en el botón de desplazamiento izquierda o derecha de una categoría de cinta de opciones, devuelve un puntero a ese botón.  
  
```  
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] El punto de prueba.  
  
### <a name="return-value"></a>Valor devuelto  
 Si *punto* está dentro del rectángulo delimitador del ya sea de la izquierda o el botón de desplazamiento a la derecha de la categoría de cinta de opciones, devuelve un puntero a ese botón o en caso contrario, devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isactive"></a>  CMFCRibbonCategory::IsActive  
 Indica si la categoría de cinta de opciones es la categoría activa en la barra de cinta de opciones.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la categoría de cinta de opciones es la categoría activa; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La categoría de cinta de opciones active muestra sus paneles de cinta.  
  
##  <a name="isvisible"></a>  CMFCRibbonCategory::IsVisible  
 Indica si la categoría de cinta de opciones está visible.  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la categoría de cinta de opciones está visible; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Categorías de cinta de opciones que están visibles muestra una pestaña de categoría.  
  
##  <a name="iswindows7look"></a>  CMFCRibbonCategory::IsWindows7Look  
 Indica si la cinta de opciones del elemento primario tiene Windows 7 buscar (botón de aplicación rectangular pequeño).  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la cinta de opciones del elemento primario tiene Windows 7 de búsqueda; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="notifycontrolcommand"></a>  CMFCRibbonCategory::NotifyControlCommand  
 Entrega un mensaje de comando WM_NOTIFY a todos los `CMFCRibbonPanel` elementos en el `CMFCRibbonCategory` hasta que se ha controlado el mensaje.  
  
```  
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,  
    int nNotifyCode,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
*bAccelerator*<br/>
[in] Es TRUE si este comando que se ha originado desde un acelerador o FALSE en caso contrario.  
  
*nNotifyCode*<br/>
[in] El código de notificación.  
  
*wParam*<br/>
[in] El campo WPARAM del mensaje.  
  
*lParam*<br/>
[in] El campo LPARAM del mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ha controlado el mensaje, o FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncancelmode"></a>  CMFCRibbonCategory::OnCancelMode  
 Invoca el modo de cancelar en todos los `CMFCRibbonPanel` elementos de la `CMFCRibbonCategory`.  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>  CMFCRibbonCategory::OnDraw  
 Lo llama el marco de trabajo para dibujar la categoría de cinta de opciones.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo para la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawimage"></a>  CMFCRibbonCategory::OnDrawImage  
 Lo llama el marco de trabajo para dibujar la imagen especificada en la categoría de cinta de opciones.  
  
```  
virtual BOOL OnDrawImage(
    CDC* pDC,  
    CRect rect,  
    CMFCRibbonBaseElement* pElement,  
    BOOL bIsLargeImage,  
    BOOL nImageIndex,  
    BOOL bCenter);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo para la imagen.  
  
*Rect*<br/>
[in] Rectángulo de presentación de la imagen.  
  
*pElement*<br/>
[in] Puntero en el elemento de la cinta que contiene la imagen.  
  
*bIsLargeImage*<br/>
[in] TRUE si la imagen es el gran tamaño; FALSE si la imagen es el tamaño pequeño.  
  
*nImageIndex*<br/>
[in] Índice de base cero de la imagen en la matriz de imagen que se encuentra en la categoría de cinta de opciones.  
  
*bCenter*<br/>
[in] TRUE para centrar la imagen en el rectángulo de presentación; FALSE para dibujar la imagen en la esquina superior izquierda del rectángulo de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawmenuborder"></a>  CMFCRibbonCategory::OnDrawMenuBorder  
 Lo llama el marco de trabajo para dibujar el borde de un menú emergente.  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] No se utiliza este parámetro.  
  
*pMenuBar*<br/>
[in] No se utiliza este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método no hace nada. Invalide este método para dibujar el borde de un menú emergente.  
  
##  <a name="onkey"></a>  CMFCRibbonCategory::OnKey  
 Lo llama el marco cuando el usuario presiona un botón de teclado.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 *NChar*  
 El código de tecla virtual para la clave que un usuario ha presionado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttondown"></a>  CMFCRibbonCategory::OnLButtonDown  
 Lo llama el marco de trabajo para recuperar el elemento de la cinta de opciones en el punto especificado cuando el usuario presiona el botón primario del mouse.  
  
```  
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero del mouse, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttonup"></a>  CMFCRibbonCategory::OnLButtonUp  
 Lo llama el marco cuando el usuario suelta el botón primario del mouse y el puntero está sobre la categoría de cinta de opciones.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onmousemove"></a>  CMFCRibbonCategory::OnMouseMove  
 Lo llama el marco cuando el puntero se mueve en la barra de cinta de opciones para actualizar la presentación de la categoría de cinta de opciones.  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
*punto*<br/>
[in] Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrtlchanged"></a>  CMFCRibbonCategory::OnRTLChanged  
 Lo llama el marco de trabajo cuando cambia el diseño de la dirección.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parámetros  
*bIsRTL*<br/>
[in] TRUE si el diseño es de derecha a izquierda; FALSE si el diseño de izquierda a derecha.  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta el diseño de todos los paneles de cinta de opciones y los elementos de la cinta de opciones que figuran en la categoría de cinta de opciones.  
  
##  <a name="onscrollhorz"></a>  CMFCRibbonCategory::OnScrollHorz  
 Se desplaza a la categoría de cinta de opciones en dirección horizontal.  
  
```  
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,  
    int nScrollOffset = 0);
```  
  
### <a name="parameters"></a>Parámetros  
*bScrollLeft*<br/>
[in] TRUE para desplazarse a la izquierda; Si es FALSE, desplácese a la derecha.  
  
*nScrollOffset*<br/>
[in] La distancia de desplazamiento en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la categoría de cinta de opciones se mueve en dirección horizontal; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdatecmdui"></a>  CMFCRibbonCategory::OnUpdateCmdUI  
 Llamadas la `OnUpdateCmdUI` función miembro en cada uno de los `CMFCRibbonPanel` elementos de la `CMFCRibbonCategory` para habilitar o deshabilitar los elementos de interfaz de usuario en ellos.  
  
```  
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,  
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parámetros  
*pCmdUI*<br/>
[in] Puntero a la `CMFCRibbonCmdUI` objeto que especifica que son elementos de la interfaz de usuario esté habilitado y que se va a deshabilitar.  
  
*pTarget*<br/>
[in] Puntero a la ventana que controla la activación o desactivación de los elementos de interfaz de usuario.  
  
*bDisableIfNoHndler*<br/>
[in] TRUE para deshabilitar el elemento de interfaz de usuario si no se define ningún controlador en un mapa de mensajes; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="recalclayout"></a>  CMFCRibbonCategory::RecalcLayout  
 Ajusta el diseño de todos los controles en la categoría de cinta de opciones.  
  
```  
virtual void RecalcLayout(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo para la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removepanel"></a>  CMFCRibbonCategory::RemovePanel  
 Quita un panel de cinta de opciones de la categoría de cinta de opciones.  
  
```cpp  
BOOL RemovePanel(
    int nIndex,  
    BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
*nIndex*<br/>
[in] El número de índice del panel que se va a quitar. Obtiene al llamar a la [CMFCRibbonCategory::GetPanelIndex](#getpanelindex) método.  
  
*bDelete*<br/>
[in] TRUE para eliminar el objeto de panel de la memoria; FALSE para quitar el objeto de panel sin eliminarlo.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
##  <a name="repospanels"></a>  CMFCRibbonCategory::ReposPanels  
 Ajusta el diseño de todos los controles en los paneles de cinta de opciones que se encuentran en la categoría de cinta de opciones.  
  
```  
virtual void ReposPanels(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo para los paneles de cinta de opciones que figuran en la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcollapseorder"></a>  CMFCRibbonCategory::SetCollapseOrder  
 Define el orden en que se contraiga los paneles de cinta de opciones de la categoría de cinta de opciones.  
  
```  
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```  
  
### <a name="parameters"></a>Parámetros  
*arCollapseOrder*<br/>
[in] Especifica el orden de contracción. La matriz contiene los índices de base cero de paneles de cinta.  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca define el orden de contracción. Sin embargo, puede personalizar este comportamiento, ya que proporciona la categoría con la lista de índices que especifica el orden de contraer.  
  
 Cuando la categoría detecta que tiene que contraer un panel de cinta, busca el siguiente elemento en la lista especificada. Si la lista está vacía o no se han especificado suficientes elementos, la categoría usa el algoritmo interno.  
  
 Por ejemplo, la categoría tiene tres paneles de cinta y se puede contraer varias veces hasta que todos los paneles se encuentran en estado contraído completamente. Puede establecer el orden de contraer siguiente: 0, 0, 2, 2. En este caso, la categoría contraerá el panel de 0 a dos veces, el panel 2 dos veces. El panel que tiene el índice de 1 sigue siendo aumentado.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el `SetCollapseOrder` método en el `CMFCRibbonCategory` clase. El ejemplo muestra cómo construir una matriz para el pedido de contraer y cómo establecer el orden de contraer en la categoría de cinta de opciones.  
  
 [!code-cpp[NVC_MFC_RibbonApp#13](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]  
  
##  <a name="setdata"></a>  CMFCRibbonCategory::SetData  
 Establece los datos definidos por el usuario va a asociar a la categoría de cinta de opciones.  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
*dwData*<br/>
[in] Los datos definidos por el usuario.  
  
##  <a name="setkeys"></a>  CMFCRibbonCategory::SetKeys  
 Keytip se asigna a la categoría de cinta de opciones.  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszKeys*<br/>
[in] El texto del elemento keytip.  
  
### <a name="remarks"></a>Comentarios  
 Sugerencias de teclas se muestran cuando el usuario presiona la tecla Alt o la tecla F10.  
  
##  <a name="setname"></a>  CMFCRibbonCategory::SetName  
 Asigna un nombre y la keytip para la categoría de cinta de opciones.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszName*<br/>
[in] El nombre y la keytip de la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer la keytip para la categoría de cinta de opciones, anexar una secuencia de escape de nueva línea seguida por los caracteres de keytip en *lpszName*.  
  
##  <a name="settabcolor"></a>  CMFCRibbonCategory:: Settabcolor  
 Establece el color de la categoría de cinta de opciones.  
  
```  
void SetTabColor(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>Parámetros  
*Color*<br/>
[in] Especifica el nuevo color de la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Color puede ser uno de los siguientes valores:  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)
