---
title: Clase CMFCRibbonGallery | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddGroup
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddSubItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::Clear
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuResize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetCompactSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetDroppedDown
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupOffset
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetLastSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetRegularSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::HasMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeEnabled
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeVertical
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnAfterChangeRect
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDraw
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnEnable
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnRTLChanged
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RedrawIcons
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RemoveItemToolTips
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SelectItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetACCData
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDrawPaletteIcon
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGallery class
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
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
ms.openlocfilehash: c4eadb9820f2d7318131cc4d197dbe28d65491c0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbongallery-class"></a>Clase CMFCRibbonGallery
Implementa galerías de cinta de estilo de Office 2007.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](#cmfcribbongallery)|Construye e inicializa un objeto `CMFCRibbonGallery`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::AddGroup](#addgroup)|Agrega un nuevo grupo a la galería.|  
|[CMFCRibbonGallery::AddSubItem](#addsubitem)|Agrega un nuevo elemento de menú al menú desplegable.|  
|[CMFCRibbonGallery::Clear](#clear)|Borra el contenido de la galería.|  
|[CMFCRibbonGallery::EnableMenuResize](#enablemenuresize)|Habilita o deshabilita el cambio de tamaño del panel de menú.|  
|[CMFCRibbonGallery::EnableMenuSideBar](#enablemenusidebar)|Habilita o deshabilita la barra lateral a la izquierda del menú emergente.|  
|[CMFCRibbonGallery::GetCompactSize](#getcompactsize)|(Invalida [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonGallery::GetDroppedDown](#getdroppeddown)|(Invalida [CMFCRibbonBaseElement::GetDroppedDown](../../mfc/reference/cmfcribbonbaseelement-class.md#getdroppeddown).)|  
|[CMFCRibbonGallery::GetGroupName](#getgroupname)|Devuelve el nombre del grupo que se encuentra en el índice especificado.|  
|[CMFCRibbonGallery::GetGroupOffset](#getgroupoffset)||  
|[CMFCRibbonGallery::GetIconsInRow](#geticonsinrow)|Devuelve el número de elementos en una fila de la Galería de la cinta de opciones.|  
|[CMFCRibbonGallery::GetItemToolTip](#getitemtooltip)|Devuelve el texto de información sobre herramientas que está asociado a un elemento de la galería.|  
|[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)|Devuelve el índice del último elemento de la galería que el usuario seleccionado.|  
|[CMFCRibbonGallery::GetPaletteID](#getpaletteid)|Devuelve el identificador de comando de la galería actual.|  
|[CMFCRibbonGallery::GetRegularSize](#getregularsize)|(Invalida [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonGallery::GetSelectedItem](#getselecteditem)||  
|[CMFCRibbonGallery::HasMenu](#hasmenu)|(Invalida [CMFCRibbonButton::HasMenu](../../mfc/reference/cmfcribbonbutton-class.md#hasmenu).)|  
|[CMFCRibbonGallery::IsButtonMode](#isbuttonmode)|Especifica si la galería se encuentra en un botón de la galería.|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](#ismenuresizeenabled)|Especifica si el cambio de tamaño de menú está habilitado o deshabilitado.|  
|[CMFCRibbonGallery::IsMenuResizeVertical](#ismenuresizevertical)||  
|[CMFCRibbonGallery::IsMenuSideBar](#ismenusidebar)|Especifica si la barra lateral está habilitada o deshabilitada.|  
|[CMFCRibbonGallery::OnAfterChangeRect](#onafterchangerect)|(Invalida `CMFCRibbonButton::OnAfterChangeRect`).|  
|[CMFCRibbonGallery::OnDraw](#ondraw)|(Invalida [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonGallery::OnEnable](#onenable)|(Invalida `CMFCRibbonBaseElement::OnEnable`).|  
|[CMFCRibbonGallery::OnRTLChanged](#onrtlchanged)|(Invalida [CMFCRibbonBaseElement::OnRTLChanged](../../mfc/reference/cmfcribbonbaseelement-class.md#onrtlchanged).)|  
|[CMFCRibbonGallery::RedrawIcons](#redrawicons)|Vuelve a dibujar la galería.|  
|[CMFCRibbonGallery::RemoveItemToolTips](#removeitemtooltips)|Quita la información sobre herramientas de todos los elementos de la galería.|  
|[CMFCRibbonGallery::SelectItem](#selectitem)||  
|[CMFCRibbonGallery::SetACCData](#setaccdata)|(Invalida [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
|[CMFCRibbonGallery::SetButtonMode](#setbuttonmode)|Especifica si se debe mostrar la Galería de la cinta de opciones como un botón de lista desplegable o como una paleta directamente en la cinta de opciones.|  
|[CMFCRibbonGallery::SetGroupName](#setgroupname)|Establece el nombre de un grupo.|  
|[CMFCRibbonGallery::SetIconsInRow](#seticonsinrow)|Define el número de elementos por fila en la galería.|  
|[CMFCRibbonGallery::SetItemToolTip](#setitemtooltip)|Establece el texto de información sobre herramientas para un elemento en la galería.|  
|[CMFCRibbonGallery::SetPalette](#setpalette)|Adjunta una paleta en una galería de la cinta de opciones.|  
|[CMFCRibbonGallery::SetPaletteID](#setpaletteid)|Define el identificador de comando que se envía en el `WM_COMMAND` de mensaje cuando se ha seleccionado un elemento de la galería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](#ondrawpaletteicon)|Llamado por el marco de trabajo cuando se dibuja un icono de la galería.|  
  
## <a name="remarks"></a>Comentarios  
 Un botón de la galería se comporta igual que un botón de menú normal excepto en que muestra una galería cuando un usuario lo abra. Cuando se selecciona un elemento en una galería, el marco de trabajo envía el `WM_COMMAND` mensaje junto con el identificador de comando del botón. Cuando se controla el mensaje, se debe llamar [CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem) para determinar qué elemento se ha seleccionado desde la galería.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonGallery` clase para configurar un `CMFCRibbonGallery` objeto. En el ejemplo se muestra cómo especificar el número de elementos por fila en la galería, ajustar el tamaño del panel de menú, habilitar la barra lateral a la izquierda del menú emergente y mostrar la Galería de la cinta de opciones como una paleta directamente en la barra de la cinta de opciones. Este fragmento de código forma parte de la [ejemplo dibujar cliente](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient Nº&6;](../../mfc/reference/codesnippet/cpp/cmfcribbongallery-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonPaletteGallery.h  
  
##  <a name="addgroup"></a>CMFCRibbonGallery::AddGroup  
 Agrega un nuevo grupo a la galería.  
  
```  
void AddGroup(
    LPCTSTR lpszGroupName,  
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    CMFCToolBarImages& imagesGroup);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    int nIconsNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszGroupName`  
 Especifica el nombre del grupo.  
  
 [in] `uiImagesPaletteResID`  
 Especifica el identificador de recurso de la lista de imágenes que contiene las imágenes para el grupo.  
  
 [in] `cxPaletteImage`  
 Especifica el ancho en píxeles de una imagen.  
  
 [in] `imagesGroup`  
 Una referencia a la lista de imágenes que contiene imágenes de grupo.  
  
 [in] `nIconsNum`  
 Especifica el número de iconos en el grupo. Este parámetro debe especificarse solo para personalizado (dibujado por el propietario) grupos.  
  
### <a name="remarks"></a>Comentarios  
 Puede dividir los elementos en la Galería de la cinta en varios grupos mediante una llamada a este método. Cada grupo puede tener una leyenda.  
  
##  <a name="addsubitem"></a>CMFCRibbonGallery::AddSubItem  
 Agrega un nuevo elemento de menú al menú desplegable.  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1,  
    BOOL bOnTop=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pSubItem`  
 Un puntero al elemento que desea agregar al menú.  
  
 [in] `nIndex`  
 Especifica el índice de base cero de una ubicación donde se inserta el elemento.  
  
 [in] `bOnTop`  
 `TRUE`para especificar que se debe insertar el elemento antes de la Galería de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede combinar galerías de elemento emergente con los elementos de menú emergente llama a este método. Elementos de menú pueden colocarse antes o después de la galería.  
  
 Para insertar el elemento antes de la galería, establecer `bOnTop` a `TRUE`. Establecer `bOnTop` a `FALSE` para insertar el elemento de la galería.  
  
> [!NOTE]
>  El parámetro `nIndex` especifica el índice de inserción en la parte superior de la galería y en la parte inferior de la galería. Por ejemplo, si necesita insertar una elemento en una posición antes de la galería, establezca `nIndex` en 1 y `bOnTop` a `TRUE`. De forma similar, si necesita insertar una elemento en una posición por debajo de la galería, establezca `nIndex` en 1 y `bOnTop` a `FALSE`.  
  
##  <a name="clear"></a>CMFCRibbonGallery::Clear  
 Borra el contenido de la galería.  
  
```  
virtual void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para quitar todo el contenido de la Galería de la cinta de opciones. Esto debe hacerse antes de adjuntar una nueva galería de la cinta o el conjunto de grupos a la Galería de la cinta de opciones.  
  
##  <a name="cmfcribbongallery"></a>CMFCRibbonGallery::CMFCRibbonGallery  
 Construye e inicializa un [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md) objeto.  
  
```  
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    UINT uiImagesPaletteResID=0,  
    int cxPaletteImage=0);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CSize sizeIcon,  
    int nIconsNum,  
    BOOL bDefaultButtonStyle=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Especifica el identificador del comando que se ejecutará cuando un usuario hace clic en el botón de comando.  
  
 `lpszText`  
 Especifica el texto que aparece en el botón.  
  
 `nSmallImageIndex`  
 Índice de base cero de la imagen aparezca en el botón.  
  
 `nLargeImageIndex`  
 Índice de base cero de la imagen aparezca en el botón grande.  
  
 `imagesPalette`  
 Una referencia a la [CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) objeto que contiene las imágenes para que aparezca en la galería.  
  
 `uiImagesPaletteResID`  
 El identificador de recurso de la lista de imágenes para mostrar en la galería.  
  
 `cxPaletteImage`  
 Especifica el ancho, en píxeles, de la imagen en la galería.  
  
 `sizeIcon`  
 Especifica el tamaño, en píxeles, de la imagen de la galería.  
  
 `nIconsNum`  
 Especifica el número de iconos en la galería.  
  
 `bDefaultButtonStyle`  
 Especifica si se utiliza el valor predeterminado o el estilo de botón dibujado por el propietario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enablemenuresize"></a>CMFCRibbonGallery::EnableMenuResize  
 Habilita o deshabilita el cambio de tamaño del panel de menú.  
  
```  
void EnableMenuResize(
    BOOL bEnable = TRUE,  
    BOOL bVertcalOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para ajustar el tamaño del menú; de lo contrario, `FALSE`.  
  
 [in] `bVertcalOnly`  
 `TRUE`para especificar que la galería puede cambiarse sólo verticalmente; `FALSE` especificar que la galería se puede cambiar el tamaño tanto vertical y horizontalmente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para habilitar o deshabilitar el cambio de tamaño de la Galería de la cinta de opciones. Cuando está habilitado el cambio de tamaño, la Galería de la cinta de opciones muestra a un agarrador que un usuario puede usar para cambiar su tamaño.  
  
##  <a name="enablemenusidebar"></a>CMFCRibbonGallery::EnableMenuSideBar  
 Habilita o deshabilita la barra lateral a la izquierda del menú emergente.  
  
```  
void EnablMenuSideBar(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para especificar que la barra lateral está habilitada; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar o deshabilitar la barra lateral del estilo de Office XP en el lado izquierdo del menú.  
  
##  <a name="getcompactsize"></a>CMFCRibbonGallery::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdroppeddown"></a>CMFCRibbonGallery::GetDroppedDown  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getgroupname"></a>CMFCRibbonGallery::GetGroupName  
 Devuelve el nombre del grupo que se encuentra en el índice especificado.  
  
```  
LPCTSTR GetGroupName(int nGroupIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nGroupIndex`  
 Especifica el índice de base cero para el grupo cuyo nombre se desea recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del grupo que se encuentra en el índice especificado. Pasar un índice no válido provocará un error de aserción.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getgroupoffset"></a>CMFCRibbonGallery::GetGroupOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetGroupOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="geticonsinrow"></a>CMFCRibbonGallery::GetIconsInRow  
 Devuelve el número de elementos en una fila de la Galería de la cinta de opciones.  
  
```  
int GetIconsInRow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en una fila.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getitemtooltip"></a>CMFCRibbonGallery::GetItemToolTip  
 Devuelve el texto de información sobre herramientas que está asociado a un elemento de la galería.  
  
```  
LPCTSTR GetItemToolTip(int nItemIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nItemIndex`  
 Especifica el índice de base cero del elemento para el que se va a recuperar el texto de información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la cadena de información sobre herramientas asignada a un elemento de la Galería de la cinta de opciones. Puede ser `NULL` si no hay información sobre herramientas se asigna a ese elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getlastselecteditem"></a>CMFCRibbonGallery::GetLastSelectedItem  
 Devuelve el índice del último elemento en la Galería de la cinta de opciones que el usuario seleccionado.  
  
```  
static int GetLastSelectedItem(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Especifica el identificador de comando del elemento de menú que abre la Galería de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Cuando el usuario selecciona un elemento en la Galería de la cinta de opciones, la biblioteca envía el `WM_COMMAND` mensaje junto con el identificador de comando del botón de menú que se abre la Galería de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpaletteid"></a>CMFCRibbonGallery::GetPaletteID  
 Devuelve el identificador de comando de la paleta actual.  
  
```  
int GetPaletteID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando de la paleta seleccionada actualmente.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getregularsize"></a>CMFCRibbonGallery::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getselecteditem"></a>CMFCRibbonGallery::GetSelectedItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasmenu"></a>CMFCRibbonGallery::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isbuttonmode"></a>CMFCRibbonGallery::IsButtonMode  
 Especifica si la paleta se encuentra en un botón de la galería.  
  
```  
BOOL IsButtonMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la paleta se muestra como un botón de menú desplegable; `FALSE` si se muestra la paleta directamente en la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenuresizeenabled"></a>CMFCRibbonGallery::IsMenuResizeEnabled  
 Especifica si está habilitado el cambio de tamaño de menú.  
  
```  
BOOL IsMenuResizeEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha habilitado el cambio de tamaño de menú; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenuresizevertical"></a>CMFCRibbonGallery::IsMenuResizeVertical  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuResizeVertical() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenusidebar"></a>CMFCRibbonGallery::IsMenuSideBar  
 Especifica si la barra lateral está habilitada o deshabilitada.  
  
```  
BOOL IsMenuSideBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra lateral del estilo de Office XP se dibuja en el lado izquierdo del menú emergente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onafterchangerect"></a>CMFCRibbonGallery::OnAfterChangeRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>CMFCRibbonGallery::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawpaletteicon"></a>CMFCRibbonGallery::OnDrawPaletteIcon  
 Llamado por el marco de trabajo cuando se dibuja un icono de la galería.  
  
```  
virtual void OnDrawPaletteIcon(
    CDC* pDC,  
    CRect rectIcon,  
    int nIconIndex,  
    CMFCRibbonGalleryIcon* pIcon,  
    COLORREF clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo que se usa para dibujar.  
  
 [in] `rectIcon`  
 Especifica el rectángulo delimitador del icono que se va a dibujar.  
  
 [in] `nIconIndex`  
 Especifica el índice de base cero en la lista de imágenes de iconos de la Galería del icono que se va a dibujar.  
  
 [in] `pIcon`  
 Un puntero al icono que se va a dibujar.  
  
 [in] `clrText`  
 Especifica el color del texto del elemento que se va a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada para personalizar la apariencia de una galería de la cinta de opciones.  
  
##  <a name="onenable"></a>CMFCRibbonGallery::OnEnable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrtlchanged"></a>CMFCRibbonGallery::OnRTLChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="redrawicons"></a>CMFCRibbonGallery::RedrawIcons  
 Vuelve a dibujar la galería.  
  
```  
void RedrawIcons();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para volver a dibujar la galería. Debe llamar a este método si se ha modificado el contenido de la galería en tiempo de ejecución.  
  
##  <a name="removeitemtooltips"></a>CMFCRibbonGallery::RemoveItemToolTips  
 Quita la información sobre herramientas de todos los elementos de la galería.  
  
```  
void RemoveItemToolTips();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="selectitem"></a>CMFCRibbonGallery::SelectItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SelectItem(int nItemIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nItemIndex`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setaccdata"></a>CMFCRibbonGallery::SetACCData  
 Rellena el objeto `CAccessibilityData` especificado mediante los datos de accesibilidad de la galería de la cinta de opciones.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,   
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
 La ventana primaria de la ventana de la galería de la cinta de opciones.  
  
 [out] `data`  
 Un objeto `CAccessibilityData` que recibe los datos de accesibilidad procedentes de la galería de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`Si el método es correcto; de lo contrario, `FALSE`.  
  
##  <a name="setbuttonmode"></a>CMFCRibbonGallery::SetButtonMode  
 Determina si se debe mostrar la Galería de la cinta de opciones como un botón de lista desplegable o como una paleta directamente en la cinta de opciones.  
  
```  
void SetButtonMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`para mostrar la Galería de la cinta de opciones como un botón de menú desplegable; `FALSE` para mostrar el contenido de la Galería de la cinta directamente en la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setgroupname"></a>CMFCRibbonGallery::SetGroupName  
 Establece el nombre de un grupo.  
  
```  
void SetGroupName(
    int nGroupIndex,  
    LPCTSTR lpszGroupName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nGroupIndex`  
 Especifica el índice de base cero para el grupo que se está cambiando el nombre.  
  
 [in] `lpszGroupName`  
 Especifica el nuevo nombre para el grupo.  
  
### <a name="remarks"></a>Comentarios  
 El grupo cuyo nombre se está cambiando debe haber agregado con el [CMFCRibbonGallery::AddGroup](#addgroup) método.  
  
##  <a name="seticonsinrow"></a>CMFCRibbonGallery::SetIconsInRow  
 Especifica el número de elementos por fila en la galería.  
  
```  
void SetIconsInRow(int nIconsInRow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIconsInRow`  
 Especifica el número de elementos que aparecen en cada fila de la galería.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para especificar el ancho de la Galería de la cinta de opciones.  
  
##  <a name="setitemtooltip"></a>CMFCRibbonGallery::SetItemToolTip  
 Establece el texto de información sobre herramientas para un elemento en la galería.  
  
```  
void SetItemToolTip(
    int nItemIndex,  
    LPCTSTR lpszToolTip);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nItemIndex`  
 Índice de base cero del elemento de paleta que desea asociar la información sobre herramientas.  
  
 [in] `lpszToolTip`  
 El texto que aparecerá en la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpalette"></a>CMFCRibbonGallery::SetPalette  
 Adjunta una paleta en una galería de la cinta de opciones.  
  
```  
void SetPalette(CMFCToolBarImages& imagesPalette);

 
void SetPalette(
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `imagesPalette`  
 Especifica la lista de imágenes que contiene los iconos para que aparezcan en la galería.  
  
 [in] `uiImagesPaletteResID`  
 Especifica el identificador de recurso de la lista de imágenes que contiene los iconos para que aparezcan en la galería.  
  
 [in] `cxPaletteImage`  
 Especifica el ancho, en píxeles, de una imagen en la galería.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpaletteid"></a>CMFCRibbonGallery::SetPaletteID  
 Define el identificador de comando que se envía en el **WM_COMMAND** mensaje cuando un usuario selecciona un elemento de la galería.  
  
```  
void SetPaletteID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador de comando que se envía en el **WM_COMMAND** mensaje cuando un usuario selecciona un elemento de la galería.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar el elemento específico que el usuario seleccionado de la galería, llame a la [CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem) método estático.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Clase CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

