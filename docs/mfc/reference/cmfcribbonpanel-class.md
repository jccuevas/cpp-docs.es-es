---
title: Clase CMFCRibbonPanel | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::CMFCRibbonPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::Add
- AFXRIBBONPANEL/CMFCRibbonPanel::AddSeparator
- AFXRIBBONPANEL/CMFCRibbonPanel::AddToolBar
- AFXRIBBONPANEL/CMFCRibbonPanel::FindByData
- AFXRIBBONPANEL/CMFCRibbonPanel::FindByID
- AFXRIBBONPANEL/CMFCRibbonPanel::GetCaptionHeight
- AFXRIBBONPANEL/CMFCRibbonPanel::GetCount
- AFXRIBBONPANEL/CMFCRibbonPanel::GetData
- AFXRIBBONPANEL/CMFCRibbonPanel::GetDefaultButton
- AFXRIBBONPANEL/CMFCRibbonPanel::GetDroppedDown
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElement
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElements
- AFXRIBBONPANEL/CMFCRibbonPanel::GetElementsByID
- AFXRIBBONPANEL/CMFCRibbonPanel::GetFocused
- AFXRIBBONPANEL/CMFCRibbonPanel::GetGalleryRect
- AFXRIBBONPANEL/CMFCRibbonPanel::GetHighlighted
- AFXRIBBONPANEL/CMFCRibbonPanel::GetIndex
- AFXRIBBONPANEL/CMFCRibbonPanel::GetItemIDsList
- AFXRIBBONPANEL/CMFCRibbonPanel::GetName
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentButton
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentCategory
- AFXRIBBONPANEL/CMFCRibbonPanel::GetParentMenuBar
- AFXRIBBONPANEL/CMFCRibbonPanel::GetPreferedMenuLocation
- AFXRIBBONPANEL/CMFCRibbonPanel::GetPressed
- AFXRIBBONPANEL/CMFCRibbonPanel::GetRect
- AFXRIBBONPANEL/CMFCRibbonPanel::GetVisibleElements
- AFXRIBBONPANEL/CMFCRibbonPanel::HasElement
- AFXRIBBONPANEL/CMFCRibbonPanel::HitTest
- AFXRIBBONPANEL/CMFCRibbonPanel::HitTestEx
- AFXRIBBONPANEL/CMFCRibbonPanel::Insert
- AFXRIBBONPANEL/CMFCRibbonPanel::InsertSeparator
- AFXRIBBONPANEL/CMFCRibbonPanel::IsCenterColumnVert
- AFXRIBBONPANEL/CMFCRibbonPanel::IsCollapsed
- AFXRIBBONPANEL/CMFCRibbonPanel::IsHighlighted
- AFXRIBBONPANEL/CMFCRibbonPanel::IsJustifyColumns
- AFXRIBBONPANEL/CMFCRibbonPanel::IsMainPanel
- AFXRIBBONPANEL/CMFCRibbonPanel::IsMenuMode
- AFXRIBBONPANEL/CMFCRibbonPanel::MakeGalleryItemVisible
- AFXRIBBONPANEL/CMFCRibbonPanel::OnKey
- AFXRIBBONPANEL/CMFCRibbonPanel::RecalcWidths
- AFXRIBBONPANEL/CMFCRibbonPanel::Remove
- AFXRIBBONPANEL/CMFCRibbonPanel::RemoveAll
- AFXRIBBONPANEL/CMFCRibbonPanel::Replace
- AFXRIBBONPANEL/CMFCRibbonPanel::ReplaceByID
- AFXRIBBONPANEL/CMFCRibbonPanel::SetCenterColumnVert
- AFXRIBBONPANEL/CMFCRibbonPanel::SetData
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementMenu
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementRTC
- AFXRIBBONPANEL/CMFCRibbonPanel::SetElementRTCByID
- AFXRIBBONPANEL/CMFCRibbonPanel::SetFocused
- AFXRIBBONPANEL/CMFCRibbonPanel::SetJustifyColumns
- AFXRIBBONPANEL/CMFCRibbonPanel::SetKeys
- AFXRIBBONPANEL/CMFCRibbonPanel::ShowPopup
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonPanel class
ms.assetid: 51d70749-1140-4386-b103-f14082049ba6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 1f833e1fa59f733734da321718d5db73377fa4bd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonpanel-class"></a>Clase CMFCRibbonPanel
Implementa un panel que contiene un conjunto de elementos de cinta. Cuando se dibuja el panel, muestra tantos elementos como es posible, dado el tamaño del panel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonPanel : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonPanel::CMFCRibbonPanel](#cmfcribbonpanel)|Construye e inicializa un objeto `CMFCRibbonPanel`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonPanel::Add](#add)|Agrega un elemento de la cinta de opciones en el panel.|  
|[CMFCRibbonPanel::AddSeparator](#addseparator)|Agrega un separador en el panel de la cinta.|  
|[CMFCRibbonPanel::AddToolBar](#addtoolbar)|Agrega una barra de herramientas en el panel de la cinta.|  
|[CMFCRibbonPanel::FindByData](#findbydata)||  
|[CMFCRibbonPanel::FindByID](#findbyid)|Devuelve un elemento identificado por un identificador de comando especificado.|  
|[CMFCRibbonPanel::GetCaptionHeight](#getcaptionheight)||  
|[CMFCRibbonPanel::GetCount](#getcount)|Devuelve el número de elementos en el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::GetData](#getdata)|Devuelve los datos definidos por el usuario asociados con el panel.|  
|[CMFCRibbonPanel::GetDefaultButton](#getdefaultbutton)||  
|[CMFCRibbonPanel::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonPanel::GetElement](#getelement)|Devuelve el elemento situado en un índice especificado de la cinta.|  
|[CMFCRibbonPanel::GetElements](#getelements)|Recupera todos los elementos que se encuentran en el panel de la cinta.|  
|[CMFCRibbonPanel::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonPanel::GetFocused](#getfocused)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonPanel::GetGalleryRect](#getgalleryrect)|Devuelve un rectángulo delimitador del elemento de galería.|  
|[CMFCRibbonPanel::GetHighlighted](#gethighlighted)||  
|[CMFCRibbonPanel::GetIndex](#getindex)||  
|[CMFCRibbonPanel::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonPanel::GetName](#getname)||  
|[CMFCRibbonPanel::GetParentButton](#getparentbutton)||  
|[CMFCRibbonPanel::GetParentCategory](#getparentcategory)|Devuelve la categoría primaria del panel de la cinta.|  
|[CMFCRibbonPanel::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonPanel::GetPreferedMenuLocation](#getpreferedmenulocation)||  
|[CMFCRibbonPanel::GetPressed](#getpressed)||  
|[CMFCRibbonPanel::GetRect](#getrect)||  
|[CMFCRibbonPanel::GetVisibleElements](#getvisibleelements)|Obtiene una matriz de elementos visibles.|  
|[CMFCRibbonPanel::HasElement](#haselement)||  
|[CMFCRibbonPanel::HitTest](#hittest)||  
|[CMFCRibbonPanel::HitTestEx](#hittestex)||  
|[CMFCRibbonPanel::Insert](#insert)|Inserta un elemento de la cinta de opciones en la posición especificada.|  
|[CMFCRibbonPanel::InsertSeparator](#insertseparator)|Inserta un separador en la posición especificada.|  
|[CMFCRibbonPanel::IsCenterColumnVert](#iscentercolumnvert)|Especifica si todos los elementos de panel se deben centrar (alineados) verticalmente, por columna.|  
|[CMFCRibbonPanel::IsCollapsed](#iscollapsed)||  
|[CMFCRibbonPanel::IsHighlighted](#ishighlighted)||  
|[CMFCRibbonPanel::IsJustifyColumns](#isjustifycolumns)|Especifica si todas las columnas del panel tienen el mismo ancho.|  
|[CMFCRibbonPanel::IsMainPanel](#ismainpanel)||  
|[CMFCRibbonPanel::IsMenuMode](#ismenumode)||  
|[CMFCRibbonPanel::MakeGalleryItemVisible](#makegalleryitemvisible)|Desplaza la Galería para mostrar el elemento especificado de la cinta de opciones.|  
|[CMFCRibbonPanel::OnKey](#onkey)||  
|[CMFCRibbonPanel::RecalcWidths](#recalcwidths)||  
|[CMFCRibbonPanel::Remove](#remove)|Quita y, opcionalmente, elimina un elemento situado en el índice especificado.|  
|[CMFCRibbonPanel::RemoveAll](#removeall)|Quita todos los elementos de panel de la cinta.|  
|[CMFCRibbonPanel::Replace](#replace)|Reemplaza un elemento a otro basándose en sus valores de índice correspondientes.|  
|[CMFCRibbonPanel::ReplaceByID](#replacebyid)|Reemplaza un elemento a otro basándose en un identificador de comando especificado.|  
|[CMFCRibbonPanel::SetCenterColumnVert](#setcentercolumnvert)|Ordena el panel para alinear elementos verticalmente, por columna.|  
|[CMFCRibbonPanel::SetData](#setdata)|Asocia datos definidos por el usuario con el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::SetElementMenu](#setelementmenu)|Asigna un menú emergente en el elemento que tiene el identificador de comando especificado.|  
|[CMFCRibbonPanel::SetElementRTC](#setelementrtc)|Agrega un elemento de la cinta especificado por la información de clase en tiempo de ejecución proporcionados en el panel de la cinta.|  
|[CMFCRibbonPanel::SetElementRTCByID](#setelementrtcbyid)|Agrega un elemento de la cinta especificado por la información de clase en tiempo de ejecución proporcionados en el panel de la cinta.|  
|[CMFCRibbonPanel::SetFocused](#setfocused)|Establece el foco en el elemento especificado de la cinta de opciones.|  
|[CMFCRibbonPanel::SetJustifyColumns](#setjustifycolumns)|Habilita o deshabilita la justificación de la columna.|  
|[CMFCRibbonPanel::SetKeys](#setkeys)|Establece el método abreviado de teclado que muestra el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::ShowPopup](#showpopup)||  
  
## <a name="remarks"></a>Comentarios  
 Paneles de cinta son agrupaciones lógicas de tareas relacionadas que cree dentro de las categorías de la cinta de opciones. El tamaño de los cambios de la cinta de opciones, el diseño del panel se ajusta automáticamente para mostrar tantos elementos como sea posible.  
  
 Puede obtener una cinta de opciones de paneles que se encuentra en una categoría de cinta de opciones mediante una llamada a la [CMFCRibbonCategory::GetPanel](../../mfc/reference/cmfcribboncategory-class.md#getpanel) método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un `CMFCRibbonPanel` objeto utilizando varios métodos en la `CMFCRibbonPanel` clase. El ejemplo muestra cómo establecer el método abreviado de teclado que muestra el panel de la cinta de opciones, alinear los elementos en el panel verticalmente por columna y habilitar la justificación de la columna. Este fragmento de código forma parte de la [ejemplo de demostración de Microsoft Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo&#10;](../../mfc/reference/codesnippet/cpp/cmfcribbonpanel-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonPanel.h  
  
##  <a name="add"></a>CMFCRibbonPanel::Add  
 Anexa el elemento especificado de la cinta de opciones a la matriz de elementos de la cinta que se encuentra en el panel de la cinta.  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pElem`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addseparator"></a>CMFCRibbonPanel::AddSeparator  
 Agrega un separador en el panel de la cinta.  
  
```  
virtual void AddSeparator();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para agregar un separador en el panel de la cinta. Se agregará el separador situado junto al elemento de la cinta de opciones que se agregó la llamada anterior a [CMFCRibbonPanel::Add](#add). Para insertar un separador en una posición determinada, llame a [CMFCRibbonPanel::InsertSeparator](#insertseparator).  
  
##  <a name="addtoolbar"></a>CMFCRibbonPanel::AddToolBar  
 Agrega una barra de herramientas en el panel de la cinta.  
  
```  
CMFCRibbonButtonsGroup* AddToolBar(
UINT uiToolbarResID,  
UINT uiColdResID = 0,  
UINT uiHotResID = 0,  
UINT uiDisabledResID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiToolbarResID`  
 Especifica el identificador de recurso de la barra de herramientas para agregar.  
  
 [in] `uiColdResID`  
 Especifica el identificador de recursos de imágenes frío de la barra de herramientas.  
  
 [in] `uiHotResID`  
 Especifica el identificador de recursos de imágenes de la barra de herramientas activas.  
  
 [in] `uiDisabledResID`  
 Especifica el identificador de recursos de imágenes de la barra de herramientas deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Llame a este método para agregar una barra de herramientas en el panel de la cinta. La barra de herramientas se agregará al lado del elemento de la cinta de opciones agregado por la llamada anterior a [CMFCRibbonPanel::Add](#add).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las barras de herramientas, imágenes activas, imágenes frías e imágenes deshabilitadas, consulte [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md).  
  
##  <a name="cmfcribbonpanel"></a>CMFCRibbonPanel::CMFCRibbonPanel  
 Construye e inicializa un [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md) objeto.  
  
```  
CMFCRibbonPanel(
LPCTSTR lpszName = NULL,  
HICON hIcon = NULL);  
  
CMFCRibbonPanel(CMFCRibbonGallery* pPaletteButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Nombre del panel de la cinta.  
  
 [in] `hIcon`  
 Controlar el icono del botón predeterminado para el panel de la cinta de opciones.  
  
 [in] `pPaletteButton`  
 Puntero a una galería de la cinta de opciones para el panel de la cinta de opciones.  
  
##  <a name="findbydata"></a>CMFCRibbonPanel::FindByData  
 Recupera el elemento de la cinta de opciones que está asociado con los datos especificados.  
  
```  
CMFCRibbonBaseElement* FindByData(DWORD_PTR dwData) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Los datos asociados a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findbyid"></a>CMFCRibbonPanel::FindByID  
 Recupera el elemento de la cinta de opciones que se identifica mediante el identificador de comando especificado.  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 El identificador de comando de un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento de la cinta de opciones que se identifica mediante el identificador de comando especificado; de lo contrario `NULL` si no se identifica ningún elemento de la cinta de opciones con el identificador de comando especificado.  
  
##  <a name="getcaptionheight"></a>CMFCRibbonPanel::GetCaptionHeight  
 Recupera el alto de un título para el panel de la cinta de opciones.  
  
```  
int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, de un título para el panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcount"></a>CMFCRibbonPanel::GetCount  
 Recupera el número de elementos de la cinta de opciones que se encuentran en el panel de la cinta.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la cinta de opciones que se encuentran en el panel de la cinta.  
  
##  <a name="getdata"></a>CMFCRibbonPanel::GetData  
 Devuelve los datos definidos por el usuario asociados con el panel.  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos definidos por el usuario asociados con el panel.  
  
##  <a name="getdefaultbutton"></a>CMFCRibbonPanel::GetDefaultButton  
 Recupera el botón predeterminado para el panel de la cinta de opciones.  
  
```  
CMFCRibbonButton& GetDefaultButton();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El botón predeterminado para el panel de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel de la cinta no tiene suficiente espacio para mostrar sus elementos de la cinta de opciones, se muestra el botón predeterminado.  
  
##  <a name="getdroppeddown"></a>CMFCRibbonPanel::GetDroppedDown  
 Recupera un puntero a un elemento de la cinta si el menú emergente está desplegado.  
  
```  
CMFCRibbonBaseElement* GetDroppedDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al elemento de cinta de opciones que tiene el menú emergente desplegado; de lo contrario `NULL` si ningún elemento de la cinta tiene su menú emergente desplegada.  
  
### <a name="remarks"></a>Comentarios  
 Se prueban los elementos de cinta que se encuentran en el panel de la cinta.  
  
##  <a name="getelement"></a>CMFCRibbonPanel::GetElement  
 Devuelve el elemento situado en un índice especificado de la cinta.  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero del elemento que se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido para el elemento de la base de la cinta de opciones que se encuentra en la posición `nIndex` en el panel de la cinta de opciones, o `NULL` si no hay ningún elemento en el índice especificado.  
  
##  <a name="getelements"></a>CMFCRibbonPanel::GetElements  
 Recupera todos los elementos de la cinta de opciones que se encuentran en el panel de la cinta.  
  
```  
void GetElements(CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `arElements`  
 Una matriz que se rellena con todos los elementos de la cinta de opciones que se encuentran en el panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getelementsbyid"></a>CMFCRibbonPanel::GetElementsByID  
 Agrega elementos de la cinta de opciones que tienen el identificador de comando especificado en la matriz especificada.  
  
```  
void GetElementsByID(
UINT uiCmdID,  
CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Identificador de comando para un elemento de la cinta de opciones.  
  
 [in] `arElements`  
 Matriz de elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Se prueban los elementos de cinta que se encuentran en el panel de la cinta.  
  
##  <a name="gethighlighted"></a>CMFCRibbonPanel::GetHighlighted  
 Recupera el elemento de la cinta de opciones que se resalta en el panel de la cinta.  
  
```  
CMFCRibbonBaseElement* GetHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al elemento de cinta de opciones que se resalta en el panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getindex"></a>CMFCRibbonPanel::GetIndex  
 Recupera el índice de base cero del elemento especificado de la cinta de opciones de la matriz de elementos de la cinta de opciones que se encuentran en el panel de la cinta.  
  
```  
virtual int GetIndex(CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pElem`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento especificado de la cinta de opciones si el método se realizó correctamente; de lo contrario, devuelve-1.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getitemidslist"></a>CMFCRibbonPanel::GetItemIDsList  
 Recupera los identificadores de comando para todos los elementos de la cinta de opciones en el panel de la cinta de opciones.  
  
```  
void GetItemIDsList(CList<UINT, UINT>& lstItems) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lstItems`  
 La lista de identificadores de comando para los elementos de cinta de opciones que se encuentran en el panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getname"></a>CMFCRibbonPanel::GetName  
 Recupera el nombre del panel de la cinta.  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre del panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getparentbutton"></a>CMFCRibbonPanel::GetParentButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getparentcategory"></a>CMFCRibbonPanel::GetParentCategory  
 Devuelve la categoría primaria del panel de la cinta.  
  
```  
CMFCRibbonCategory* GetParentCategory() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la categoría de cinta que contiene el panel de la cinta.  
  
##  <a name="getparentmenubar"></a>CMFCRibbonPanel::GetParentMenuBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpreferedmenulocation"></a>CMFCRibbonPanel::GetPreferedMenuLocation  
 Recupera el rectángulo de presentación preferido para el menú emergente del panel de la cinta.  
  
```  
virtual BOOL GetPreferedMenuLocation(CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rect`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve siempre `FALSE`. Invalide este método para recuperar el rectángulo de presentación preferido para el menú emergente del panel de la cinta.  
  
##  <a name="getpressed"></a>CMFCRibbonPanel::GetPressed  
 Recupera un puntero a un elemento de la cinta de opciones en el panel de la cinta si el usuario presiona actualmente.  
  
```  
CMFCRibbonBaseElement* GetPressed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento de la cinta si el usuario presiona actualmente de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrect"></a>CMFCRibbonPanel::GetRect  
 Recupera el rectángulo de presentación para el panel de la cinta de opciones.  
  
```  
const CRect& GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo de presentación para el panel de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="haselement"></a>CMFCRibbonPanel::HasElement  
 Indica si el panel de la cinta de opciones contiene el elemento especificado de la cinta de opciones.  
  
```  
BOOL HasElement(const CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pElem`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de la cinta de opciones contiene el elemento especificado de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="highlight"></a>CMFCRibbonPanel::Highlight  
 Establece el color de resaltado para el panel de la cinta seleccionada y para el elemento de la cinta especificada por el punto.  
  
```  
virtual void Highlight(
BOOL bHighlight,  
CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHighlight`  
 `TRUE`para resaltar el panel de la cinta; `FALSE` a unhighlight el panel de la cinta.  
  
 [in] `point`  
 Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hittest"></a>CMFCRibbonPanel::HitTest  
 Recupera un elemento de la cinta si el punto especificado se encuentra en ella.  
  
```  
virtual CMFCRibbonBaseElement* HitTest(
CPoint point,  
BOOL bCheckPanelCaption = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
 [in] `bCheckPanelCaption`  
 `TRUE`Para probar el título del panel de cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de la cinta si el punto especificado se encuentra en él; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Se prueban los elementos de cinta que se encuentran en el panel de la cinta.  
  
##  <a name="hittestex"></a>CMFCRibbonPanel::HitTestEx  
 Recupera el índice de base cero del elemento de cinta de opciones que tiene el punto especificado ubicado en ella.  
  
```  
virtual int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Las coordenadas x e y del puntero, en relación con la esquina superior izquierda de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento de cinta de opciones que tiene el punto especificado que se encuentra en él; de lo contrario, devuelve-1.  
  
### <a name="remarks"></a>Comentarios  
 Se prueban los elementos de cinta que se encuentran en el panel de la cinta.  
  
##  <a name="insert"></a>CMFCRibbonPanel::Insert  
 Inserta el elemento de la cinta especificada en la posición especificada de la matriz de elementos de cinta que se encuentra en el panel de la cinta.  
  
```  
virtual BOOL Insert(
CMFCRibbonBaseElement* pElem,  
int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pElem`  
 Puntero a un elemento de la cinta de opciones.  
  
 [in] `nIndex`  
 Valor de base cero, comprendido entre -1 y el número de elementos de la cinta de opciones que se encuentran en la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta se ha insertado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de `nIndex` es -1, o si `nIndex` es igual al número de elementos de la cinta de opciones de la matriz, el elemento de la cinta especificada se agrega al final de la matriz. Si el valor de `nIndex` está fuera del intervalo, el método producirá un error.  
  
##  <a name="insertseparator"></a>CMFCRibbonPanel::InsertSeparator  
 Inserta un separador en la posición especificada.  
  
```  
virtual BOOL InsertSeparator(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero donde se inserta el separador.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el separador se ha insertado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para insertar un separador en la posición especificada por `nIndex`. Para insertar un separador situado junto al elemento de la cinta de opciones agregado más recientemente, llame a [CMFCRibbonPanel::AddSeparator](#addseparator).  
  
##  <a name="iscentercolumnvert"></a>CMFCRibbonPanel::IsCenterColumnVert  
 Indica si las posiciones verticales de los elementos de la cinta se centran dentro de su rectángulo de presentación.  
  
```  
BOOL IsCenterColumnVert() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si coloca la vertical de elementos de la cinta se centran dentro de su rectángulo de presentación; de lo contrario, `FALSE`.  
  
##  <a name="iscollapsed"></a>CMFCRibbonPanel::IsCollapsed  
 Indica si el tamaño de pantalla de panel de la cinta está minimizado en dirección horizontal.  
  
```  
BOOL IsCollapsed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el tamaño de pantalla de panel de la cinta se minimiza en la dirección horizontal; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se contrae un panel de cinta de opciones, sólo muestra el botón de manera predeterminada, su nombre y una flecha de lista desplegable.  
  
##  <a name="ishighlighted"></a>CMFCRibbonPanel::IsHighlighted  
 Indica si se resalta la visualización del panel de la cinta.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se resalta la visualización del panel de la cinta; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La presentación de un panel de cinta de opciones aparece resaltada cuando el puntero está sobre él.  
  
##  <a name="isjustifycolumns"></a>CMFCRibbonPanel::IsJustifyColumns  
 Indica si las dimensiones de visualización de elementos de la cinta de opciones que se encuentran en la misma columna en el panel de la cinta de opciones se establecen en el mismo ancho.  
  
```  
BOOL IsJustifyColumns() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las dimensiones de visualización de elementos de la cinta de opciones que se encuentran en la misma columna en el panel de la cinta de opciones se establecen en el mismo ancho; de lo contrario, `FALSE`.  
  
##  <a name="ismainpanel"></a>CMFCRibbonPanel::IsMainPanel  
 Indica si el panel de la cinta es el panel principal de la cinta de opciones.  
  
```  
virtual BOOL IsMainPanel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve siempre `FALSE`. Invalide este método para indicar si el panel de la cinta es el panel principal de la cinta de opciones.  
  
 El panel principal de la cinta de opciones se muestra cuando el usuario selecciona el botón de la aplicación.  
  
##  <a name="ismenumode"></a>CMFCRibbonPanel::IsMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onkey"></a>CMFCRibbonPanel::OnKey  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nChar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="recalcwidths"></a>CMFCRibbonPanel::RecalcWidths  
 Vuelve a calcular el ancho de cada configuración de diseño de pantalla del panel de la cinta de opciones.  
  
```  
virtual void RecalcWidths(
CDC* pDC,  
int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el panel de la cinta de opciones.  
  
 [in] `nHeight`  
 Alto del panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
 Un panel de cinta de opciones cambia su configuración de diseño cuando cambie el ancho disponible.  
  
##  <a name="remove"></a>CMFCRibbonPanel::Remove  
 Quita y, opcionalmente, elimina un elemento situado en el índice especificado.  
  
```  
BOOL Remove(
int nIndex,  
BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero del elemento que se quita del panel de la cinta.  
  
 [in] `bDelete`  
 `TRUE`Para eliminar el elemento que se va a quitar; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento se quita y se elimina (si `bDelete` es `TRUE`); `FALSE` si no se quitó el elemento o si no hay ningún elemento de la cinta se encuentra en `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para quitar un elemento del panel de la cinta.  
  
##  <a name="removeall"></a>CMFCRibbonPanel::RemoveAll  
 Elimina todos los elementos de la cinta de opciones del panel de la cinta.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos de la cinta de opciones se eliminan desde el panel de la cinta y se destruye.  
  
##  <a name="replace"></a>CMFCRibbonPanel::Replace  
 Reemplaza un elemento a otro basándose en su valor de índice.  
  
```  
BOOL Replace(
int nIndex,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero del elemento que se va a reemplazar.  
  
 [in] [out]`pElem`  
 Un puntero válido para el elemento que reemplaza el elemento original.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta original se ha reemplazado correctamente por el nuevo elemento de la cinta de opciones; `FALSE` si no se reemplaza el elemento de la cinta, o si no hay ningún elemento en el índice especificado.  
  
### <a name="remarks"></a>Comentarios  
 Para reemplazar un elemento de la cinta por el identificador de comando, llame a [CMFCRibbonPanel::ReplaceByID](#replacebyid).  
  
##  <a name="replacebyid"></a>CMFCRibbonPanel::ReplaceByID  
 Reemplaza un elemento a otro basándose en un identificador de comando especificado.  
  
```  
BOOL ReplaceByID(
UINT uiCmdID,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Especifica el identificador de comando del elemento para reemplazar.  
  
 [in] [out]`pElem`  
 Un puntero válido para el elemento que va a reemplazar el elemento original.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta original se ha reemplazado correctamente por el nuevo elemento de la cinta de opciones; `FALSE` si no se reemplaza el elemento de la cinta de opciones o si realmente no existe ningún elemento con el identificador de comando especificado.  
  
### <a name="remarks"></a>Comentarios  
 Para reemplazar un elemento de la cinta de opciones en función de posición, llame a [CMFCRibbonPanel::Replace](#replace).  
  
##  <a name="setcentercolumnvert"></a>CMFCRibbonPanel::SetCenterColumnVert  
 Habilita o deshabilita el centro de las posiciones verticales de los elementos de la cinta de opciones dentro de su rectángulo de presentación.  
  
```  
void SetCenterColumnVert(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`Para centrar las posiciones verticales de los elementos de la cinta de opciones dentro de su rectángulo de presentación; `FALSE` para deshabilitar esta característica.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdata"></a>CMFCRibbonPanel::SetData  
 Asocia datos definidos por el usuario con el panel de la cinta de opciones.  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Especifica los datos definidos por el usuario para establecer.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para asociar datos definidos por el usuario en el panel de la cinta.  
  
##  <a name="setelementmenu"></a>CMFCRibbonPanel::SetElementMenu  
 Asigna un menú emergente en el elemento que tiene el identificador de comando especificado.  
  
```  
BOOL SetElementMenu(
UINT uiCmdID,  
HMENU hMenu,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);

 
BOOL SetElementMenu(
UINT uiCmdID,  
UINT uiMenuResID,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Especifica el identificador de comando del elemento de cinta de opciones en el menú se agrega.  
  
 [in] `hMenu`  
 Especifica el identificador del menú de Windows para agregar al panel de la cinta.  
  
 [in] `bIsDefautCommand`  
 `TRUE`para especificar que debe ejecutarse el comando asociado con el elemento de la cinta si se hace clic en el elemento de la cinta de opciones. En este caso, sólo se abre el menú cuando el usuario hace clic en la flecha situada junto al elemento de la cinta de opciones. `FALSE`para especificar que no se debe ejecutar el comando asociado al elemento de la cinta de opciones si se hace clic en el elemento de la cinta de opciones. En este caso, el menú emergente aparece independientemente de donde el usuario hace clic en el elemento.  
  
 [in] `bRightAlign`  
 `TRUE`para especificar que el menú emergente está alineado a la derecha; de lo contrario, `FALSE`.  
  
 [in] `uiMenuResID`  
 Especifica el identificador de recurso del menú para agregar al panel de la cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú se ha asignado al elemento de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para asignar un menú emergente en el elemento de cinta de opciones que tiene el identificador de comando especificado.  
  
##  <a name="setelementrtc"></a>CMFCRibbonPanel::SetElementRTC  
 Agrega el elemento de la cinta especificada por la información de clase en tiempo de ejecución proporcionados en el panel de la cinta.  
  
```  
CMFCRibbonBaseElement* SetElementRTC(
int nIndex,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero del elemento de cinta de opciones para agregar.  
  
 [in] [out]`pRTC`  
 Puntero a la información de clase en tiempo de ejecución para el elemento de la cinta de opciones que se agrega al panel de la cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento de la cinta que se creó utilizando la información de clase en tiempo de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Si desea agregar un elemento personalizado (por ejemplo, un botón de color) al panel de cinta de opciones, debe especificar la información de clase en tiempo de ejecución del elemento personalizado. La cinta de opciones almacena esta información, se crea el elemento personalizado y reemplaza un elemento existente que se encuentra (identificada mediante) el identificador del comando especificado. La cinta de opciones, a continuación, devuelve un puntero al elemento recién creado.  
  
##  <a name="setelementrtcbyid"></a>CMFCRibbonPanel::SetElementRTCByID  
 Agrega un elemento de la cinta especificada por la información de clase en tiempo de ejecución proporcionados en el panel de la cinta.  
  
```  
CMFCRibbonBaseElement* SetElementRTCByID(
UINT uiCmdID,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Especifica el identificador de comando del elemento de la cinta de opciones para agregar.  
  
 [in] [out]`pRTC`  
 Puntero a la información de clase en tiempo de ejecución asociado al elemento de la cinta de opciones que se agrega al panel de la cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento de la cinta que se creó utilizando la información de clase en tiempo de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Si desea agregar un elemento personalizado (por ejemplo, un botón de color) al panel de cinta de opciones, debe especificar la información de clase en tiempo de ejecución del elemento personalizado. La cinta de opciones almacena esta información, crea el elemento personalizado y reemplaza un elemento existente que se encuentra el identificador del comando especificado. A continuación, devuelve un puntero al elemento recién creado.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetElementRTCByID` método:  
  
```  
 
// Load and add toolbar with standard buttons. This toolbar  
// should display a custom color button with id ID_CHAR_COLOR:  
 
pPanel->AddToolBar(IDR_MAINFRAME,
    IDB_MAINFRAME256);

CMFCRibbonColorButton* pColorButton = 
(CMFCRibbonColorButton*)pPanel->SetElementRTCByID(
ID_CHAR_COLOR,
    RUNTIME_CLASS (CMFCRibbonColorButton));

 
// SetElementRTCByID sets runtime class and returns a pointer  
// to the newly created custom button,
    which can be set up immediately:  
pColorButton->EnableAutomaticButton(_T("Automatic"),
    RGB (0,
    0,
    0));  
```  
  
##  <a name="setjustifycolumns"></a>CMFCRibbonPanel::SetJustifyColumns  
 Habilita o deshabilita el ajuste del ancho de los elementos de la cinta en la misma columna.  
  
```  
void SetJustifyColumns(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`Para ajustar el ancho de los elementos de la cinta de opciones en la misma columna al ancho del elemento más grande de cinta de opciones en la columna; `FALSE` para deshabilitar el ajuste de ancho.  
  
### <a name="remarks"></a>Comentarios  
 Cuando esta característica está habilitada en un panel de cinta de opciones, los anchos de elementos de la cinta de opciones en la misma columna se ajustan al ancho del elemento más grande de cinta en la misma columna.  
  
##  <a name="setkeys"></a>CMFCRibbonPanel::SetKeys  
 Establece la keytip para el botón predeterminado del panel de la cinta.  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszKeys`  
 La sugerencia de tecla para el botón predeterminado del panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel de la cinta no tiene suficiente espacio para mostrar sus elementos de la cinta de opciones, se muestra el botón predeterminado.  
  
##  <a name="showpopup"></a>CMFCRibbonPanel::ShowPopup  
 Crea y muestra un menú emergente del panel de la cinta de opciones.  
  
```  
CMFCRibbonPanelMenu* ShowPopup(CMFCRibbonDefaultPanelButton* pButton = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero al botón predeterminado para el panel de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al menú emergente para el panel de la cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 El menú emergente del panel de cinta sólo está disponible cuando se contrae la visualización del panel de la cinta.  
  
##  <a name="setfocused"></a>CMFCRibbonPanel::SetFocused  
 Establece el foco en el elemento especificado de la cinta de opciones.  
  
```  
void SetFocused(CMFCRibbonBaseElement* pNewFocus);
```  
  
### <a name="parameters"></a>Parámetros  
 `pNewFocus`  
 Puntero a un elemento de cinta que recibe el foco.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="makegalleryitemvisible"></a>CMFCRibbonPanel::MakeGalleryItemVisible  
 Desplaza la Galería para mostrar el elemento especificado de la cinta de opciones.  
  
```  
void MakeGalleryItemVisible(CMFCRibbonBaseElement* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Un puntero a un elemento de la cinta de opciones para mostrar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="iswindows7look"></a>CMFCRibbonPanel::IsWindows7Look  
 Indica si la cinta de opciones primario tiene Windows 7 buscar (botón pequeña aplicación rectangular).  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la cinta de opciones primario tiene Windows 7 de búsqueda; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getvisibleelements"></a>CMFCRibbonPanel::GetVisibleElements  
 Recupera una matriz de elementos visibles.  
  
```  
void GetVisibleElements(
CArray<CMFCRibbonBaseElement*,  
CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 `arElements`  
 Cuando la función vuelve, este parámetro contiene una matriz de elementos visibles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getgalleryrect"></a>CMFCRibbonPanel::GetGalleryRect  
 Devuelve un rectángulo delimitador de un elemento de la galería.  
  
```  
CRect GetGalleryRect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tamaño y posición de la Galería de este panel.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getfocused"></a>CMFCRibbonPanel::GetFocused  
 Devuelve un elemento que tiene el foco.  
  
```  
CMFCRibbonBaseElement* GetFocused() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento enfocado o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Clase de CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)   
 [Clase CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

