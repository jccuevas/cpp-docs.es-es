---
title: Clase CMFCRibbonBaseElement | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonBaseElement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonBaseElement class
ms.assetid: 419ea91b-5062-44cc-b0a3-f87d29566f62
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
ms.openlocfilehash: c596d7ef6ba87ca0f084c03856cf4f54dc8eac49
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbaseelement-class"></a>Clase CMFCRibbonBaseElement
El `CMFCRibbonBaseElement` clase es la clase base para todos los elementos que puede agregar a un [barra ribbon](../../mfc/reference/cmfcribbonbar-class.md). Los botones, las casillas y los cuadros combinados de la cinta son ejemplos de elementos de la cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonBaseElement : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonBaseElement`|Construye un objeto `CMFCRibbonBaseElement`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBaseElement::AddToKeyList](#addtokeylist)|Agrega una matriz de sugerencias de teclas keytip para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::AddToListBox](#addtolistbox)|Agrega un elemento de la cinta de opciones en el cuadro de lista de comandos de la cinta especificada.|  
|[CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar](#canbeaddedtoquickaccesstoolbar)|Indica si el elemento de la cinta de opciones se puede agregar a la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::CanBeCompacted](#canbecompacted)|Indica si el tamaño del elemento de la cinta de opciones puede ser compacto.|  
|[CMFCRibbonBaseElement::CanBeStretched](#canbestretched)|Indica si el alto del elemento de la cinta de opciones puede aumentar verticalmente a la altura de una fila de la cinta de opciones.|  
|[CMFCRibbonBaseElement::CanBeStretchedHorizontally](#canbestretchedhorizontally)|Indica si se puede cambiar el ancho del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::CleanUpSizes](#cleanupsizes)|Limpia la configuración de dimensión para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::ClosePopupMenu](#closepopupmenu)|Cierra el menú emergente para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::CopyFrom](#copyfrom)|Copia el estado de especificado `CMFCRibbonBaseElement` al objeto actual.|  
|[CMFCRibbonBaseElement::DestroyCtrl](#destroyctrl)|Destruye el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::DrawImage](#drawimage)|Dibuja la imagen para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::Find](#find)|Devuelve el puntero especificado para el elemento de la cinta si señala al objeto actual.|  
|[CMFCRibbonBaseElement::FindByData](#findbydata)|Recupera un puntero al elemento de la cinta de opciones si contiene los datos especificados.|  
|[CMFCRibbonBaseElement::FindByID](#findbyid)|Recupera un puntero al elemento de la cinta de opciones si ese elemento identificado por el identificador del comando especificado.|  
|[CMFCRibbonBaseElement::FindByOriginal](#findbyoriginal)|Recupera un puntero al elemento de la cinta de opciones si su elemento de la cinta original coincide con el elemento especificado de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetCompactSize](#getcompactsize)|Devuelve el tamaño compacto del elemento de la cinta.|  
|[CMFCRibbonBaseElement::GetData](#getdata)|Recupera los datos definidos por el usuario asociados con el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetDescription](#getdescription)|Devuelve la descripción del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetDroppedDown](#getdroppeddown)|Recupera un puntero al elemento de la cinta de opciones si su menú emergente está desplegada.|  
|[CMFCRibbonBaseElement::GetElements](#getelements)|Agrega el elemento actual de la cinta de opciones en la matriz especificada.|  
|[CMFCRibbonBaseElement::GetElementsByID](#getelementsbyid)|Agrega el elemento actual de la cinta de opciones en la matriz especificada, si el elemento actual de la cinta de opciones contiene el identificador del comando especificado.|  
|[CMFCRibbonBaseElement::GetHighlighted](#gethighlighted)|Recupera un puntero al elemento de la cinta de opciones si está resaltado.|  
|[CMFCRibbonBaseElement::GetID](#getid)|Devuelve el identificador de comando del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetImageSize](#getimagesize)|Devuelve el tamaño de la imagen del elemento de la cinta.|  
|[CMFCRibbonBaseElement::GetIntermediateSize](#getintermediatesize)|Devuelve el tamaño del elemento de la cinta en su estado intermedio.|  
|[CMFCRibbonBaseElement::GetKeys](#getkeys)|Devuelve la keytip asociada al elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetKeyTipRect](#getkeytiprect)|Recupera el rectángulo de límite keytip para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetKeyTipSize](#getkeytipsize)|Recupera el tamaño del texto de información.|  
|[CMFCRibbonBaseElement::GetLocationInGroup](#getlocationingroup)|Indica la ubicación de visualización del elemento de cinta de opciones en un grupo de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetMenuKeys](#getmenukeys)|Devuelve las sugerencias de teclas asociado con un botón.|  
|[CMFCRibbonBaseElement::GetNotifyID](#getnotifyid)|Recupera el identificador de comando de notificación para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetOriginal](#getoriginal)|Recupera el elemento de la cinta original.|  
|[CMFCRibbonBaseElement::GetParentCategory](#getparentcategory)|Recupera la categoría de cinta de opciones para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetParentPanel](#getparentpanel)|Recupera el panel de la cinta que contiene el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetParentRibbonBar](#getparentribbonbar)|Recupera la barra de cinta primario para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetParentWnd](#getparentwnd)|Recupera la ventana primaria para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetPressed](#getpressed)|Recupera un puntero al elemento de cinta si el usuario presiona actualmente.|  
|[CMFCRibbonBaseElement::GetQuickAccessToolBarID](#getquickaccesstoolbarid)|Recupera el identificador de comando del elemento de la cinta de opciones cuando se encuentra en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::GetRect](#getrect)|Devuelve el rectángulo delimitador del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta.|  
|[CMFCRibbonBaseElement::GetSize](#getsize)|Devuelve el tamaño actual del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetText](#gettext)|Devuelve el texto asociado al elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetToolTipText](#gettooltiptext)|Devuelve el texto de información sobre herramientas del elemento de la cinta.|  
|[CMFCRibbonBaseElement::GetTopLevelRibbonBar](#gettoplevelribbonbar)|Recupera la barra de la cinta de opciones de nivel superior para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::HasCompactMode](#hascompactmode)|Especifica si el elemento de la cinta tiene un modo compacto.|  
|[CMFCRibbonBaseElement::HasFocus](#hasfocus)|Indica si el elemento primario tiene el foco de teclado.|  
|[CMFCRibbonBaseElement::HasIntermediateMode](#hasintermediatemode)|Especifica si el elemento de la cinta tiene un modo intermedio.|  
|[CMFCRibbonBaseElement::HasLargeMode](#haslargemode)|Especifica si el elemento de la cinta de opciones tiene un modo de gran tamaño.|  
|[CMFCRibbonBaseElement::HasMenu](#hasmenu)|Indica si el elemento de la cinta de opciones tiene un menú.|  
|[CMFCRibbonBaseElement::HitTest](#hittest)|Recupera un puntero al elemento de cinta si el punto especificado se encuentra en ella.|  
|[CMFCRibbonBaseElement::IsAlignByColumn](#isalignbycolumn)|Indica si el elemento de la cinta se alinea verticalmente con otros elementos de la cinta de opciones.|  
|[CMFCRibbonBaseElement::IsAlwaysLargeImage](#isalwayslargeimage)|Indica si el tamaño de la imagen de elemento de cinta siempre es grande.|  
|[CMFCRibbonBaseElement::IsAutoRepeatMode](#isautorepeatmode)|Indica si el elemento de la cinta está en modo de repetición automática.|  
|[CMFCRibbonBaseElement::IsChecked](#ischecked)|Especifica si el elemento de la cinta de opciones está activado.|  
|[CMFCRibbonBaseElement::IsCompactMode](#iscompactmode)|Especifica si el elemento de la cinta está en un modo compacto.|  
|[CMFCRibbonBaseElement::IsDefaultMenuLook](#isdefaultmenulook)||  
|[CMFCRibbonBaseElement::IsDisabled](#isdisabled)|Especifica si el elemento de la cinta de opciones está deshabilitado.|  
|[CMFCRibbonBaseElement::IsDroppedDown](#isdroppeddown)|Determina si el elemento de la cinta de opciones muestra un menú emergente y está desplegado.|  
|[CMFCRibbonBaseElement::IsFocused](#isfocused)|Especifica si el elemento de la cinta de opciones tiene el foco.|  
|[CMFCRibbonBaseElement::IsGalleryIcon](#isgalleryicon)|Indica si el elemento de la cinta se encuentra en una galería de la cinta de opciones.|  
|[CMFCRibbonBaseElement::IsHighlighted](#ishighlighted)|Especifica si se resalta el elemento de la cinta.|  
|[CMFCRibbonBaseElement::IsIntermediateMode](#isintermediatemode)|Indica si la imagen para el elemento de la cinta actual es de tamaño intermedio.|  
|[CMFCRibbonBaseElement::IsLargeMode](#islargemode)|Indica si la imagen actual para el elemento de la cinta es de gran tamaño.|  
|[CMFCRibbonBaseElement::IsMenuMode](#ismenumode)|Indica si el elemento de la cinta se encuentra en un menú.|  
|[CMFCRibbonBaseElement::IsPressed](#ispressed)|Indica si el usuario ha hecho clic en el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::IsQATMode](#isqatmode)|Indica si el elemento de la cinta se encuentra en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::IsSeparator](#isseparator)|Indica si el elemento de la cinta es un separador de presentación.|  
|[CMFCRibbonBaseElement::IsShowGroupBorder](#isshowgroupborder)|Indica si el elemento de la cinta se encuentra en un grupo que muestra un borde común.|  
|[CMFCRibbonBaseElement::IsShowTooltipOnBottom](#isshowtooltiponbottom)|Indica si la información sobre herramientas se muestra en el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::IsTabStop](#istabstop)|Indica si se puede seleccionar el elemento de la cinta de opciones con el teclado.|  
|[CMFCRibbonBaseElement::IsTextAlwaysOnRight](#istextalwaysonright)|Indica si el texto del elemento de la cinta de opciones se muestra en la parte derecha.|  
|[CMFCRibbonBaseElement::IsVisible](#isvisible)|Indica si el elemento de la cinta se muestra actualmente.|  
|[CMFCRibbonBaseElement::IsWholeRowHeight](#iswholerowheight)|Indica si la heigth de visualización del elemento de la cinta de opciones es el mismo que el alto de pantalla del panel de la cinta que lo contiene.|  
|[CMFCRibbonBaseElement::NotifyCommand](#notifycommand)|Envía una notificación de comando a la ventana primaria del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::NotifyHighlightListItem](#notifyhighlightlistitem)|Notifica a la ventana primaria de la barra de la cinta de opciones cuando un usuario resalta un elemento de cinta que se encuentra en una lista.|  
|[CMFCRibbonBaseElement::OnAddToQAToolbar](#onaddtoqatoolbar)|Agrega el elemento de la cinta de opciones en la barra de herramientas de acceso rápido especificado.|  
|[CMFCRibbonBaseElement::OnAfterChangeRect](#onafterchangerect)|Actualiza la información sobre herramientas para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::OnAutoRepeat](#onautorepeat)|Actualiza el elemento de la cinta de opciones en respuesta a la entrada de usuario sostenido.|  
|[CMFCRibbonBaseElement::OnCalcTextSize](#oncalctextsize)|Calcula el tamaño del texto para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::OnChangeMenuHighlight](#onchangemenuhighlight)|Llamado por el marco de trabajo cuando cambia el resaltado de un elemento de la cinta de opciones que se encuentra en un menú.|  
|[CMFCRibbonBaseElement::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta.|  
|[CMFCRibbonBaseElement::OnDrawKeyTip](#ondrawkeytip)|Llamado por el marco para dibujar la keytip para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::OnDrawMenuImage](#ondrawmenuimage)|Lo llama el marco de trabajo cuando se dibuja la imagen del menú del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::OnDrawOnList](#ondrawonlist)|Llamado por el marco para dibujar el elemento de la cinta de opciones en un cuadro de lista de comandos.|  
|[CMFCRibbonBaseElement::OnKey](#onkey)|Lo llama el marco de trabajo cuando el usuario presiona keytip y el elemento de la cinta de opciones tiene el foco.|  
|[CMFCRibbonBaseElement::OnMenuKey](#onmenukey)||  
|[CMFCRibbonBaseElement::OnRTLChanged](#onrtlchanged)|Llamado por el marco de trabajo cuando el diseño cambia de dirección.|  
|[CMFCRibbonBaseElement::OnShow](#onshow)|Llamado por el marco de trabajo para mostrar u ocultar el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::OnShowPopupMenu](#onshowpopupmenu)|Llamado por el marco de trabajo cuando el elemento de la cinta de opciones se va a mostrar un menú emergente.|  
|[CMFCRibbonBaseElement::PostMenuCommand](#postmenucommand)||  
|[CMFCRibbonBaseElement::Redraw](#redraw)|Actualiza la presentación del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetACCData](#setaccdata)|Establece los datos de accesibilidad para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetCompactMode](#setcompactmode)|Establece el tamaño de presentación para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetData](#setdata)|Asocia un elemento de datos con el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetDefaultMenuLook](#setdefaultmenulook)||  
|[CMFCRibbonBaseElement::SetDescription](#setdescription)|Establece la descripción del elemento de la cinta.|  
|[CMFCRibbonBaseElement::SetID](#setid)|Establece el identificador de comando del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetInitialMode](#setinitialmode)|Establece el tamaño inicial del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetKeys](#setkeys)|Establece la keytip para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetOriginal](#setoriginal)|Establece el elemento de la cinta original para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetParentCategory](#setparentcategory)|Establece la categoría primaria para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetParentMenu](#setparentmenu)|Establece al elemento primario de contenedor de menú para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetParentRibbonBar](#setparentribbonbar)|Establece la barra de cinta primario para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetRect](#setrect)|Establece el fot dimensiones que Mostrar rectángulo para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetText](#settext)|Establece el texto para el elemento de la cinta.|  
|[CMFCRibbonBaseElement::SetTextAlwaysOnRight](#settextalwaysonright)|Establece el texto del elemento de la cinta de opciones Mostrar de la derecha.|  
|[CMFCRibbonBaseElement::SetToolTipText](#settooltiptext)|Establece el texto de información sobre herramientas para el elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::SetVisible](#setvisible)|Establece el estado de visibilidad del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::StretchHorizontally](#stretchhorizontally)|Ajusta el ancho del elemento de la cinta de opciones.|  
|[CMFCRibbonBaseElement::StretchToWholeRow](#stretchtowholerow)|Cambia el alto del elemento de la cinta de opciones para el alto de fila especificado.|  
|[CMFCRibbonBaseElement::UpdateTooltipInfo](#updatetooltipinfo)|Actualiza el texto de información sobre herramientas mediante el recurso de comando para el elemento de la cinta de opciones.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBaseElement::OnProcessKey](#onprocesskey)|Lo llama el marco de trabajo cuando el usuario presiona una tecla de método abreviado.|  
|[CMFCRibbonBaseElement::OnSetFocus](#onsetfocus)|Llamado por el marco cuando un elemento de cinta recibe o pierde el foco de entrada.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCRibbonBaseElement` clase define las propiedades que son comunes a todos los elementos de la cinta de opciones que incluyen el identificador de comando, etiqueta de texto, el texto de información sobre herramientas, una descripción del elemento y estado (que puede ser centrado, resaltado, presionado, deshabilitado, activada o desplegada).  
  
 El tamaño de la imagen de un elemento de la cinta de opciones está definido por el `RibbonImageType` miembro, que puede ser uno de los siguientes valores:  
  
- `RibbonImageLarge`  
  
- `RibbonImageSmall`  
  
 Dependiendo de su tamaño, un elemento de la cinta de opciones muestra una imagen pequeña o grande.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonBaseElement` clase. En el ejemplo se muestra cómo obtener un `CMFCRibbonBaseElement` objeto a partir de un `CMFCRibbonStatusBar` clase, establecer la descripción del elemento de la cinta de opciones, establecer el texto, establecer la keytip y establecer el texto de información sobre herramientas para el elemento de la cinta de opciones. Este fragmento de código forma parte de la [ejemplo dibujar cliente](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient Nº&8;](../../mfc/reference/codesnippet/cpp/cmfcribbonbaseelement-class_1.cpp)]  
[!code-cpp[NVC_MFC_DrawClient&#9;](../../mfc/reference/codesnippet/cpp/cmfcribbonbaseelement-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbaseribbonelement.h  
  
##  <a name="a-nameaddtokeylista--cmfcribbonbaseelementaddtokeylist"></a><a name="addtokeylist"></a>CMFCRibbonBaseElement::AddToKeyList  
 Agrega una matriz de sugerencias de teclas keytip para el elemento de la cinta de opciones.  
  
```  
virtual void AddToKeyList(
    CArray<CMFCRibbonKeyTip*, CMFCRibbonKeyTip*>& arElems);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `arElems`  
 Hacer referencia a un [CArray](../../mfc/reference/carray-class.md) de sugerencias de teclas.  
  
### <a name="remarks"></a>Comentarios  
 Cuando está habilitada la característica de sugerencias de teclas de la cinta de opciones, el marco de trabajo muestra información sobre las teclas cinta cuando el usuario presiona la tecla ALT o la tecla F10.  
  
##  <a name="a-nameaddtolistboxa--cmfcribbonbaseelementaddtolistbox"></a><a name="addtolistbox"></a>CMFCRibbonBaseElement::AddToListBox  
 Agrega un elemento de la cinta de opciones en el cuadro de lista de comandos de la cinta especificada.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndListBox`  
 Puntero a un cuadro de lista de comandos.  
  
 [in] `bDeep`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento agregado de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo agrega elementos de cinta de opciones a un cuadro de lista de comandos para permitir al usuario personalizar la interfaz de usuario.  
  
##  <a name="a-namecanbeaddedtoquickaccesstoolbara--cmfcribbonbaseelementcanbeaddedtoquickaccesstoolbar"></a><a name="canbeaddedtoquickaccesstoolbar"></a>CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar  
 Indica si el elemento de la cinta de opciones se puede agregar a la barra de herramientas de acceso rápido.  
  
```  
virtual BOOL CanBeAddedToQuickAccessToolBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede agregar el elemento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecanbecompacteda--cmfcribbonbaseelementcanbecompacted"></a><a name="canbecompacted"></a>CMFCRibbonBaseElement::CanBeCompacted  
 Indica si el tamaño del elemento de la cinta de opciones puede ser compacto.  
  
```  
virtual BOOL CanBeCompacted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el tamaño del elemento de la cinta de opciones puede ser compacto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de un elemento de la cinta de opciones puede ser compact, intermedio o grande.  
  
##  <a name="a-namecanbestretcheda--cmfcribbonbaseelementcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonBaseElement::CanBeStretched  
 Indica si el alto del elemento de la cinta de opciones puede aumentar verticalmente a la altura de una fila de la cinta de opciones.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `TRUE`. Invalide este método para indicar si el alto del elemento de la cinta de opciones puede aumentar verticalmente a la altura de una fila de la cinta de opciones.  
  
##  <a name="a-namecanbestretchedhorizontallya--cmfcribbonbaseelementcanbestretchedhorizontally"></a><a name="canbestretchedhorizontally"></a>CMFCRibbonBaseElement::CanBeStretchedHorizontally  
 Indica si se puede cambiar el ancho del elemento de la cinta de opciones.  
  
```  
virtual BOOL CanBeStretchedHorizontally();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método para indicar si se puede cambiar el ancho del elemento de la cinta de opciones.  
  
##  <a name="a-namecleanupsizesa--cmfcribbonbaseelementcleanupsizes"></a><a name="cleanupsizes"></a>CMFCRibbonBaseElement::CleanUpSizes  
 Limpia la configuración de dimensión para el elemento de la cinta de opciones.  
  
```  
virtual void CleanUpSizes();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método en una clase derivada para restablecer la configuración de dimensión para el elemento de la cinta de opciones.  
  
##  <a name="a-nameclosepopupmenua--cmfcribbonbaseelementclosepopupmenu"></a><a name="closepopupmenu"></a>CMFCRibbonBaseElement::ClosePopupMenu  
 Cierra el menú emergente para el elemento de la cinta de opciones.  
  
```  
virtual void ClosePopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecopyfroma--cmfcribbonbaseelementcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonBaseElement::CopyFrom  
 Copia el estado de especificado [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) al objeto actual.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 El origen de [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedestroyctrla--cmfcribbonbaseelementdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonBaseElement::DestroyCtrl  
 Destruye el elemento de la cinta de opciones.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método en una clase derivada para destruir el elemento de la cinta de opciones.  
  
##  <a name="a-namedrawimagea--cmfcribbonbaseelementdrawimage"></a><a name="drawimage"></a>CMFCRibbonBaseElement::DrawImage  
 Dibuja la imagen para el elemento de la cinta de opciones.  
  
```  
virtual void DrawImage(
    CDC* pDC,  
    RibbonImageType type,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `type`  
 Valor enumerado de un tipo de imagen. Vea la sección Comentarios para obtener una lista de valores posibles.  
  
 [in] `rectImage`  
 El rectángulo de la imagen.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método en una clase derivada para dibujar la imagen para el elemento de la cinta de opciones.  
  
 La tabla siguiente enumeran los valores posibles para el `type` parámetro:  
  
 `RibbonImageLarge`  
 Tamaño de imagen de 32 x 32 píxeles.  
  
 `RibbonImageSmall`  
 Tamaño pequeño de imagen 16 x 16 píxeles.  
  
##  <a name="a-namefinda--cmfcribbonbaseelementfind"></a><a name="find"></a>CMFCRibbonBaseElement::Find  
 Devuelve el puntero especificado apunta al objeto actual.  
  
```  
virtual CMFCRibbonBaseElement* Find(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pElement`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de la cinta de opciones si `pElement` señala al objeto actual; en caso contrario `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindbydataa--cmfcribbonbaseelementfindbydata"></a><a name="findbydata"></a>CMFCRibbonBaseElement::FindByData  
 Recupera un puntero al elemento de la cinta de opciones si contiene los datos especificados.  
  
```  
virtual CMFCRibbonBaseElement* FindByData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Los datos asociados a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones si contiene los datos especificados; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindbyida--cmfcribbonbaseelementfindbyid"></a><a name="findbyid"></a>CMFCRibbonBaseElement::FindByID  
 Recupera un puntero al elemento de la cinta de opciones si ese elemento identificado por el identificador del comando especificado.  
  
```  
virtual CMFCRibbonBaseElement* FindByID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Identificador de comando para un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones si ese elemento identificado por el identificador de comando especificado; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindbyoriginala--cmfcribbonbaseelementfindbyoriginal"></a><a name="findbyoriginal"></a>CMFCRibbonBaseElement::FindByOriginal  
 Recupera un puntero al elemento actual de la cinta de opciones si su elemento de la cinta original coincide con el elemento especificado de la cinta de opciones.  
  
```  
virtual CMFCRibbonBaseElement* FindByOriginal(CMFCRibbonBaseElement* pOriginal);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOriginal`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones si su elemento de la cinta original coincide con el elemento especificado de la cinta de opciones; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la cinta de opciones que se copian en otro contenedor conservan un puntero para el elemento de la cinta original.  
  
##  <a name="a-namegetcompactsizea--cmfcribbonbaseelementgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonBaseElement::GetCompactSize  
 Devuelve el tamaño compacto del elemento de la cinta.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño compacto de un elemento de la cinta de opciones.  
  
> [!NOTE]
>  El tamaño compacto significa que el elemento de la cinta se trunca (se muestra una pequeña imagen o una imagen sin texto).  
  
##  <a name="a-namegetdataa--cmfcribbonbaseelementgetdata"></a><a name="getdata"></a>CMFCRibbonBaseElement::GetData  
 Recupera los datos definidos por el usuario asociados con el elemento de la cinta de opciones.  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos definidos por el usuario asociados con el elemento de la cinta de opciones.  
  
##  <a name="a-namegetdescriptiona--cmfcribbonbaseelementgetdescription"></a><a name="getdescription"></a>CMFCRibbonBaseElement::GetDescription  
 Devuelve la descripción del elemento de la cinta de opciones.  
  
```  
virtual CString GetDescription() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La descripción de elemento de la cinta de opciones. La descripción se muestra en la barra de estado, o en una información sobre herramientas o en el botón de menú si el elemento de la cinta se encuentra en la [CMFCRibbonMainPanel clase](../../mfc/reference/cmfcribbonmainpanel-class.md).  
  
##  <a name="a-namegetdroppeddowna--cmfcribbonbaseelementgetdroppeddown"></a><a name="getdroppeddown"></a>CMFCRibbonBaseElement::GetDroppedDown  
 Recupera un puntero al elemento de la cinta de opciones si su menú emergente está desplegada.  
  
```  
virtual CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta si se quita el menú emergente. de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetelementsa--cmfcribbonbaseelementgetelements"></a><a name="getelements"></a>CMFCRibbonBaseElement::GetElements  
 Agrega el elemento actual de la cinta de opciones en la matriz especificada.  
  
```  
virtual void GetElements(
    CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `arElements`  
 Una matriz de elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetelementsbyida--cmfcribbonbaseelementgetelementsbyid"></a><a name="getelementsbyid"></a>CMFCRibbonBaseElement::GetElementsByID  
 Agrega el elemento actual de la cinta de opciones en la matriz especificada, si el elemento actual de la cinta de opciones contiene el identificador del comando especificado.  
  
```  
virtual void GetElementsByID(
    UINT uiCmdID,  
    CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Id. de comando de un elemento de la cinta de opciones.  
  
 [in] `arElements`  
 Una matriz de elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegethighlighteda--cmfcribbonbaseelementgethighlighted"></a><a name="gethighlighted"></a>CMFCRibbonBaseElement::GetHighlighted  
 Recupera un puntero al elemento de la cinta de opciones si está resaltado.  
  
```  
virtual CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones si está resaltado; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetida--cmfcribbonbaseelementgetid"></a><a name="getid"></a>CMFCRibbonBaseElement::GetID  
 Devuelve el identificador de comando del elemento de la cinta de opciones.  
  
```  
UINT GetID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando del elemento de la cinta de opciones.  
  
##  <a name="a-namegetimagesizea--cmfcribbonbaseelementgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonBaseElement::GetImageSize  
 Devuelve el tamaño de la imagen del elemento de la cinta.  
  
```  
virtual CSize GetImageSize(RibbonImageType R) const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de la imagen del elemento de la cinta de opciones.  
  
##  <a name="a-namegetintermediatesizea--cmfcribbonbaseelementgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonBaseElement::GetIntermediateSize  
 Devuelve el tamaño del elemento de la cinta en su estado intermedio.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del elemento de cinta de opciones en su estado intermedio.  
  
##  <a name="a-namegetkeysa--cmfcribbonbaseelementgetkeys"></a><a name="getkeys"></a>CMFCRibbonBaseElement::GetKeys  
 Devuelve la keytip asociada al elemento de la cinta de opciones.  
  
```  
LPCTSTR GetKeys() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Keytip asociado al elemento de la cinta de opciones.  
  
##  <a name="a-namegetkeytiprecta--cmfcribbonbaseelementgetkeytiprect"></a><a name="getkeytiprect"></a>CMFCRibbonBaseElement::GetKeyTipRect  
 Recupera el rectángulo de límite keytip para el elemento de la cinta de opciones.  
  
```  
virtual CRect GetKeyTipRect(
    CDC* pDC,  
    BOOL bIsMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `bIsMenu`  
 `TRUE`Si el elemento de la cinta de opciones muestra un menú emergente; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve un rectángulo con valores de 0.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para devolver el rectángulo de límite keytip.  
  
##  <a name="a-namegetkeytipsizea--cmfcribbonbaseelementgetkeytipsize"></a><a name="getkeytipsize"></a>CMFCRibbonBaseElement::GetKeyTipSize  
 Recupera el tamaño del texto de información.  
  
```  
virtual CSize GetKeyTipSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del texto de información.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetlocationingroupa--cmfcribbonbaseelementgetlocationingroup"></a><a name="getlocationingroup"></a>CMFCRibbonBaseElement::GetLocationInGroup  
 Indica la ubicación de visualización del elemento de cinta de opciones en un grupo de la cinta de opciones.  
  
```  
RibbonElementLocation GetLocationInGroup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `RibbonElementLocation` valor enumerado. La tabla siguiente enumeran los valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`RibbonElementNotInGroup`|El elemento de la cinta no está contenido en un grupo de la cinta de opciones.|  
|`RibbonElementSingleInGroup`|El elemento de la cinta se muestra como el único elemento en un grupo de la cinta de opciones.|  
|`RibbonElementFirstInGroup`|El elemento de la cinta se muestra en el extremo izquierdo de un grupo de la cinta de opciones.|  
|`RibbonElementLastInGroup`|El elemento de la cinta se muestra en el extremo derecho de un grupo de la cinta de opciones.|  
|`RibbonElementMiddleInGroup`|No se muestra el elemento de la cinta de opciones en cualquiera de los extremos de un grupo de la cinta de opciones.|  
  
### <a name="remarks"></a>Comentarios  
 Grupos de elementos de la cinta de opciones solo están alineados horizontalmente.  
  
##  <a name="a-namegetmenukeysa--cmfcribbonbaseelementgetmenukeys"></a><a name="getmenukeys"></a>CMFCRibbonBaseElement::GetMenuKeys  
 Devuelve la sugerencia de tecla de menú para el elemento de la cinta de opciones.  
  
```  
LPCTSTR GetMenuKeys() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La sugerencia de tecla de menú asociado al elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se invoca, keytip menú muestra un menú emergente.  
  
##  <a name="a-namegetnotifyida--cmfcribbonbaseelementgetnotifyid"></a><a name="getnotifyid"></a>CMFCRibbonBaseElement::GetNotifyID  
 Recupera el identificador de comando de notificación para el elemento de la cinta de opciones.  
  
```  
virtual UINT GetNotifyID();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del comando de notificación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetoriginala--cmfcribbonbaseelementgetoriginal"></a><a name="getoriginal"></a>CMFCRibbonBaseElement::GetOriginal  
 Recupera el elemento de la cinta original.  
  
```  
CMFCRibbonBaseElement* GetOriginal() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento original de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la cinta de opciones que se copian en otro contenedor conservan un puntero para el elemento de la cinta original.  
  
##  <a name="a-namegetparentcategorya--cmfcribbonbaseelementgetparentcategory"></a><a name="getparentcategory"></a>CMFCRibbonBaseElement::GetParentCategory  
 Recupera la categoría de cinta de opciones para el elemento de la cinta de opciones.  
  
```  
CMFCRibbonCategory* GetParentCategory() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparentpanela--cmfcribbonbaseelementgetparentpanel"></a><a name="getparentpanel"></a>CMFCRibbonBaseElement::GetParentPanel  
 Recupera el panel de la cinta que contiene el elemento de la cinta de opciones.  
  
```  
virtual CMFCRibbonPanel* GetParentPanel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al panel de la cinta que contiene el elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparentribbonbara--cmfcribbonbaseelementgetparentribbonbar"></a><a name="getparentribbonbar"></a>CMFCRibbonBaseElement::GetParentRibbonBar  
 Recupera la barra de cinta primario para el elemento de la cinta de opciones.  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la barra de cinta primario para el elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparentwnda--cmfcribbonbaseelementgetparentwnd"></a><a name="getparentwnd"></a>CMFCRibbonBaseElement::GetParentWnd  
 Recupera la ventana primaria para el elemento de la cinta de opciones.  
  
```  
virtual CWnd* GetParentWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana primaria para el elemento de la cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 La ventana principal de un elemento de cinta es un [CMFCRibbonBar clase](../../mfc/reference/cmfcribbonbar-class.md) o un [CMFCRibbonPanelMenuBar](http://msdn.microsoft.com/en-us/7bd4b986-8b7b-493e-9746-bd3161b78581).  
  
##  <a name="a-namegetpresseda--cmfcribbonbaseelementgetpressed"></a><a name="getpressed"></a>CMFCRibbonBaseElement::GetPressed  
 Recupera un puntero al elemento de cinta si el usuario presiona actualmente.  
  
```  
virtual CMFCRibbonBaseElement* GetPressed();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta si el usuario presiona actualmente de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetquickaccesstoolbarida--cmfcribbonbaseelementgetquickaccesstoolbarid"></a><a name="getquickaccesstoolbarid"></a>CMFCRibbonBaseElement::GetQuickAccessToolBarID  
 Recupera el identificador de comando del elemento de la cinta de opciones cuando se encuentra en la barra de herramientas de acceso rápido.  
  
```  
virtual UINT GetQuickAccessToolBarID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando del elemento de cinta de opciones cuando se encuentra en la barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetrecta--cmfcribbonbaseelementgetrect"></a><a name="getrect"></a>CMFCRibbonBaseElement::GetRect  
 Devuelve el rectángulo delimitador del elemento de la cinta de opciones.  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo delimitador del elemento de la cinta de opciones. Es la posición del rectángulo en las coordenadas del elemento primario de control de la cinta de opciones.  
  
##  <a name="a-namegetregularsizea--cmfcribbonbaseelementgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonBaseElement::GetRegularSize  
 Devuelve el tamaño normal del elemento de la cinta.  
  
```  
virtual CSize GetRegularSize(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño normal del elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El tamaño normal es el tamaño máximo posible del elemento de la cinta de opciones.  
  
##  <a name="a-namegetsizea--cmfcribbonbaseelementgetsize"></a><a name="getsize"></a>CMFCRibbonBaseElement::GetSize  
 Devuelve el tamaño actual del elemento de la cinta de opciones.  
  
```  
virtual CSize GetSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño actual del elemento de la cinta de opciones.  
  
##  <a name="a-namegettexta--cmfcribbonbaseelementgettext"></a><a name="gettext"></a>CMFCRibbonBaseElement::GetText  
 Devuelve el texto asociado al elemento de la cinta de opciones.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto asociado al elemento de la cinta de opciones.  
  
##  <a name="a-namegettooltiptexta--cmfcribbonbaseelementgettooltiptext"></a><a name="gettooltiptext"></a>CMFCRibbonBaseElement::GetToolTipText  
 Devuelve el texto de información sobre herramientas del elemento de la cinta.  
  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto del elemento de la cinta de opciones.  
  
##  <a name="a-namegettoplevelribbonbara--cmfcribbonbaseelementgettoplevelribbonbar"></a><a name="gettoplevelribbonbar"></a>CMFCRibbonBaseElement::GetTopLevelRibbonBar  
 Recupera la barra de la cinta de opciones de nivel superior para el elemento de la cinta de opciones.  
  
```  
CMFCRibbonBar* GetTopLevelRibbonBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de la cinta de opciones de nivel superior para el elemento de la cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehascompactmodea--cmfcribbonbaseelementhascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonBaseElement::HasCompactMode  
 Especifica si el elemento de la cinta tiene un modo compacto.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones tiene un modo compacto. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el modo compacto, un elemento muestra una pequeña imagen.  
  
##  <a name="a-namehasintermediatemodea--cmfcribbonbaseelementhasintermediatemode"></a><a name="hasintermediatemode"></a>CMFCRibbonBaseElement::HasIntermediateMode  
 Especifica si el elemento de la cinta tiene un modo intermedio.  
  
```  
virtual BOOL HasIntermediateMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones tiene un modo intermedio, `FALSE` en caso contrario. En el modo intermedio, un elemento muestra una imagen pequeña y texto a la derecha de la imagen.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehaslargemodea--cmfcribbonbaseelementhaslargemode"></a><a name="haslargemode"></a>CMFCRibbonBaseElement::HasLargeMode  
 Determina si el elemento de la cinta tiene un modo grande.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones tiene un modo de gran tamaño. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de gran tamaño, un elemento puede hacer la altura total del panel primario.  
  
##  <a name="a-namehasmenua--cmfcribbonbaseelementhasmenu"></a><a name="hasmenu"></a>CMFCRibbonBaseElement::HasMenu  
 Indica si el elemento de la cinta de opciones tiene un menú.  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método en una clase derivada para indicar si el elemento de la cinta de opciones tiene un menú.  
  
##  <a name="a-namehittesta--cmfcribbonbaseelementhittest"></a><a name="hittest"></a>CMFCRibbonBaseElement::HitTest  
 Recupera un puntero al elemento de cinta si el punto especificado se encuentra en ella.  
  
```  
virtual CMFCRibbonBaseElement* HitTest(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones, si existe; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve un puntero válido para el elemento de la cinta de opciones cuando existe. Invalide este método para indicar si el punto está situado en el elemento de la cinta de opciones.  
  
##  <a name="a-nameisalignbycolumna--cmfcribbonbaseelementisalignbycolumn"></a><a name="isalignbycolumn"></a>CMFCRibbonBaseElement::IsAlignByColumn  
 Indica si el elemento de la cinta se alinea verticalmente con otros elementos de la cinta de opciones.  
  
```  
virtual BOOL IsAlignByColumn() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `TRUE`. Invalide este método en una clase derivada para indicar si el elemento de la cinta de opciones derivada se alinea verticalmente con otros elementos de la cinta de opciones.  
  
##  <a name="a-nameisalwayslargeimagea--cmfcribbonbaseelementisalwayslargeimage"></a><a name="isalwayslargeimage"></a>CMFCRibbonBaseElement::IsAlwaysLargeImage  
 Indica si el tamaño de la imagen de elemento de cinta siempre es grande.  
  
```  
virtual BOOL IsAlwaysLargeImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones de tamaño de imagen siempre es grande; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Tamaño de la imagen grande es 32 x 32 píxeles.  
  
##  <a name="a-nameisautorepeatmodea--cmfcribbonbaseelementisautorepeatmode"></a><a name="isautorepeatmode"></a>CMFCRibbonBaseElement::IsAutoRepeatMode  
 Indica si el elemento de la cinta está en modo de repetición automática.  
  
```  
virtual BOOL IsAutoRepeatMode(int& nDelay) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nDelay`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método para indicar si el elemento de la cinta está en modo de repetición automática.  
  
 Auto modo de repetición, el elemento de la cinta de opciones responde a un intervalo fijo, medido en milisegundos, a la entrada del usuario sostenido.  
  
##  <a name="a-nameischeckeda--cmfcribbonbaseelementischecked"></a><a name="ischecked"></a>CMFCRibbonBaseElement::IsChecked  
 Especifica si el elemento de la cinta de opciones está activado.  
  
```  
virtual BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones está activado; de lo contrario, `FALSE`.  
  
##  <a name="a-nameiscompactmodea--cmfcribbonbaseelementiscompactmode"></a><a name="iscompactmode"></a>CMFCRibbonBaseElement::IsCompactMode  
 Especifica si el elemento de la cinta está en un modo compacto.  
  
```  
BOOL IsCompactMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta está en un modo compacto; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisdefaultmenulooka--cmfcribbonbaseelementisdefaultmenulook"></a><a name="isdefaultmenulook"></a>CMFCRibbonBaseElement::IsDefaultMenuLook  
 Indica si el elemento de la cinta de opciones se establece para que aparezca como un comando emergente.  
  
```  
BOOL IsDefaultMenuLook() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el elemento de la cinta de opciones para que aparezca como un comando emergente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdisableda--cmfcribbonbaseelementisdisabled"></a><a name="isdisabled"></a>CMFCRibbonBaseElement::IsDisabled  
 Especifica si el elemento de la cinta de opciones está deshabilitado.  
  
```  
virtual BOOL IsDisabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones está deshabilitado; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisdroppeddowna--cmfcribbonbaseelementisdroppeddown"></a><a name="isdroppeddown"></a>CMFCRibbonBaseElement::IsDroppedDown  
 Especifica si el elemento de la cinta de opciones muestra un menú emergente y está desplegado.  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones está desplegado y muestra un menú emergente; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisfocuseda--cmfcribbonbaseelementisfocused"></a><a name="isfocused"></a>CMFCRibbonBaseElement::IsFocused  
 Especifica si el elemento de la cinta de opciones tiene el foco.  
  
```  
virtual BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta de opciones tiene el foco; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisgalleryicona--cmfcribbonbaseelementisgalleryicon"></a><a name="isgalleryicon"></a>CMFCRibbonBaseElement::IsGalleryIcon  
 Indica si el elemento de la cinta se encuentra en una galería de la cinta de opciones.  
  
```  
virtual BOOL IsGalleryIcon() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método en una clase derivada para indicar si el elemento de la cinta se encuentra en una galería de la cinta de opciones.  
  
##  <a name="a-nameishighlighteda--cmfcribbonbaseelementishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonBaseElement::IsHighlighted  
 Especifica si se resalta el elemento de la cinta.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se resalta el elemento de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisintermediatemodea--cmfcribbonbaseelementisintermediatemode"></a><a name="isintermediatemode"></a>CMFCRibbonBaseElement::IsIntermediateMode  
 Indica si la imagen para el elemento de la cinta actual es de tamaño intermedio.  
  
```  
BOOL IsIntermediateMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen para el elemento de la cinta es de tamaño intermedio; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Tamaño de la imagen intermedio es 16 x 16 píxeles.  
  
##  <a name="a-nameislargemodea--cmfcribbonbaseelementislargemode"></a><a name="islargemode"></a>CMFCRibbonBaseElement::IsLargeMode  
 Indica si la imagen actual para el elemento de la cinta es de gran tamaño.  
  
```  
BOOL IsLargeMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen para el elemento de la cinta es de gran tamaño; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Tamaño de la imagen grande es 32 x 32 píxeles.  
  
##  <a name="a-nameismenumodea--cmfcribbonbaseelementismenumode"></a><a name="ismenumode"></a>CMFCRibbonBaseElement::IsMenuMode  
 Indica si el elemento de la cinta se encuentra en un menú.  
  
```  
BOOL IsMenuMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se encuentra el elemento de la cinta de opciones en un menú; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameispresseda--cmfcribbonbaseelementispressed"></a><a name="ispressed"></a>CMFCRibbonBaseElement::IsPressed  
 Indica si el usuario ha hecho clic en el elemento de la cinta de opciones.  
  
```  
virtual BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el usuario hace clic en el elemento de la cinta de opciones; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisqatmodea--cmfcribbonbaseelementisqatmode"></a><a name="isqatmode"></a>CMFCRibbonBaseElement::IsQATMode  
 Indica si el elemento de la cinta se encuentra en la barra de herramientas de acceso rápido.  
  
```  
BOOL IsQATMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta se encuentra en la barra de herramientas de acceso rápido; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisseparatora--cmfcribbonbaseelementisseparator"></a><a name="isseparator"></a>CMFCRibbonBaseElement::IsSeparator  
 Indica si el elemento de la cinta es un separador de presentación.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta es un separador de presentación; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisshowgroupbordera--cmfcribbonbaseelementisshowgroupborder"></a><a name="isshowgroupborder"></a>CMFCRibbonBaseElement::IsShowGroupBorder  
 Indica si el elemento de la cinta se encuentra en un grupo que muestra un borde común.  
  
```  
BOOL IsShowGroupBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta se encuentra en un grupo que muestra un borde comunes; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisshowtooltiponbottoma--cmfcribbonbaseelementisshowtooltiponbottom"></a><a name="isshowtooltiponbottom"></a>CMFCRibbonBaseElement::IsShowTooltipOnBottom  
 Indica si la información sobre herramientas se muestra en el elemento de la cinta de opciones.  
  
```  
virtual BOOL IsShowTooltipOnBottom() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la información sobre herramientas se muestra en el elemento de la cinta de opciones; `FALSE` si la información sobre herramientas se muestra junto al puntero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameistabstopa--cmfcribbonbaseelementistabstop"></a><a name="istabstop"></a>CMFCRibbonBaseElement::IsTabStop  
 Indica si se puede seleccionar el elemento de la cinta de opciones con el teclado.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `TRUE`. Invalide este método para indicar si se puede seleccionar el elemento de la cinta de opciones con el teclado.  
  
##  <a name="a-nameistextalwaysonrighta--cmfcribbonbaseelementistextalwaysonright"></a><a name="istextalwaysonright"></a>CMFCRibbonBaseElement::IsTextAlwaysOnRight  
 Indica si el texto del elemento de la cinta de opciones se muestra en la parte derecha.  
  
```  
BOOL IsTextAlwaysOnRight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el texto del elemento de la cinta de opciones se muestra en la derecha. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisvisiblea--cmfcribbonbaseelementisvisible"></a><a name="isvisible"></a>CMFCRibbonBaseElement::IsVisible  
 Indica si el elemento de la cinta se muestra actualmente.  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta se muestra actualmente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiswholerowheighta--cmfcribbonbaseelementiswholerowheight"></a><a name="iswholerowheight"></a>CMFCRibbonBaseElement::IsWholeRowHeight  
 Indica si el alto del elemento de la cinta de opciones es el mismo que el alto de pantalla del panel de la cinta que lo contiene.  
  
```  
virtual BOOL IsWholeRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método para indicar si el alto del elemento de la cinta de opciones es el mismo que el alto de pantalla del panel de la cinta que lo contiene.  
  
##  <a name="a-namenotifycommanda--cmfcribbonbaseelementnotifycommand"></a><a name="notifycommand"></a>CMFCRibbonBaseElement::NotifyCommand  
 Envía una notificación de comando a la ventana primaria del elemento de la cinta de opciones.  
  
```  
BOOL NotifyCommand(BOOL bWithDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bWithDelay`  
 `TRUE`Para agregar la notificación de comando a la cola de mensajes de la ventana primaria; `FALSE` para enviar el mensaje inmediatamente a la ventana primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha enviado el mensaje; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namenotifyhighlightlistitema--cmfcribbonbaseelementnotifyhighlightlistitem"></a><a name="notifyhighlightlistitem"></a>CMFCRibbonBaseElement::NotifyHighlightListItem  
 Notifica a la ventana primaria de la barra de la cinta de opciones cuando un usuario resalta un elemento de cinta que se encuentra en una lista.  
  
```  
virtual void NotifyHighlightListItem(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice del elemento de cinta de opciones en la lista.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonaddtoqatoolbara--cmfcribbonbaseelementonaddtoqatoolbar"></a><a name="onaddtoqatoolbar"></a>CMFCRibbonBaseElement::OnAddToQAToolbar  
 Agrega el elemento de la cinta de opciones en la barra de herramientas de acceso rápido especificado.  
  
```  
virtual BOOL OnAddToQAToolbar(CMFCRibbonQuickAccessToolBar& qat);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `qat`  
 La barra de herramientas de acceso rápido.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE` que indica el elemento de la cinta se ha agregado a la barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonafterchangerecta--cmfcribbonbaseelementonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonBaseElement::OnAfterChangeRect  
 Actualiza la información sobre herramientas para el elemento de la cinta de opciones.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método actualiza la información sobre herramientas para el elemento de la cinta de opciones. Invalide este método para actualizar el elemento de la cinta después de que ha cambiado su rectángulo de presentación.  
  
##  <a name="a-nameonautorepeata--cmfcribbonbaseelementonautorepeat"></a><a name="onautorepeat"></a>CMFCRibbonBaseElement::OnAutoRepeat  
 Actualiza el elemento de la cinta de opciones en respuesta a la entrada de usuario sostenido.  
  
```  
virtual BOOL OnAutoRepeat();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método devuelven siempre `FALSE`. Invalide este método para procesar la entrada de usuario sostenido.  
  
##  <a name="a-nameoncalctextsizea--cmfcribbonbaseelementoncalctextsize"></a><a name="oncalctextsize"></a>CMFCRibbonBaseElement::OnCalcTextSize  
 Calcula el tamaño del texto para el elemento de la cinta de opciones.  
  
```  
virtual void OnCalcTextSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método para calcular el tamaño del texto para el elemento de la cinta de opciones.  
  
##  <a name="a-nameonchangemenuhighlighta--cmfcribbonbaseelementonchangemenuhighlight"></a><a name="onchangemenuhighlight"></a>CMFCRibbonBaseElement::OnChangeMenuHighlight  
 Llamado por el marco de trabajo cuando cambia el resaltado de un elemento de la cinta de opciones que se encuentra en un menú.  
  
```  
virtual void OnChangeMenuHighlight(CMFCRibbonPanelMenuBar* pPanelMenuBar  
    CMFCRibbonBaseElement* pHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPanelMenuBar`  
 Este parámetro no se utiliza.  
  
 [in] `pHot`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método para actualizar un elemento de cinta que se encuentra en un menú cuando cambia el resaltado.  
  
##  <a name="a-nameondrawa--cmfcribbonbaseelementondraw"></a><a name="ondraw"></a>CMFCRibbonBaseElement::OnDraw  
 Llamado por el marco de trabajo para dibujar el elemento de la cinta.  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea personalizar el dibujo de un elemento específico de la cinta de opciones.  
  
##  <a name="a-nameondrawkeytipa--cmfcribbonbaseelementondrawkeytip"></a><a name="ondrawkeytip"></a>CMFCRibbonBaseElement::OnDrawKeyTip  
 Llamado por el marco para dibujar la keytip para el elemento de la cinta de opciones.  
  
```  
virtual void OnDrawKeyTip(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bIsMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Rectángulo delimitador para la keytip.  
  
 [in] `bIsMenu`  
 `TRUE`Si la keytip es para un botón de menú emergente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenuimagea--cmfcribbonbaseelementondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonBaseElement::OnDrawMenuImage  
 Lo llama el marco de trabajo cuando se dibuja la imagen del menú del elemento de la cinta de opciones.  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Rectángulo de imagen del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE` para indicar que se dibuja la imagen.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawonlista--cmfcribbonbaseelementondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonBaseElement::OnDrawOnList  
 Llamado por el marco para dibujar el elemento de la cinta de opciones en un cuadro de lista de comandos.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el elemento de la cinta de opciones.  
  
 [in] `strText`  
 El texto para mostrar.  
  
 [in] `nTextOffset`  
 Distancia, en píxeles, del lado izquierdo del cuadro de lista para el texto para mostrar.  
  
 [in] `rect`  
 El rectángulo de presentación para el elemento de la cinta de opciones.  
  
 [in] `bIsSelected`  
 Este parámetro no se utiliza.  
  
 [in] `bHighlighted`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de lista de comandos muestra los elementos de la cinta de opciones para permitir a los usuarios personalizar la barra de herramientas de acceso rápido.  
  
##  <a name="a-nameonkeya--cmfcribbonbaseelementonkey"></a><a name="onkey"></a>CMFCRibbonBaseElement::OnKey  
 Lo llama el marco de trabajo cuando el usuario presiona keytip y el elemento de la cinta de opciones tiene el foco.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsMenuKey`  
 `TRUE`Si la keytip muestra un menú emergente; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se controló el evento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonmenukeya--cmfcribbonbaseelementonmenukey"></a><a name="onmenukey"></a>CMFCRibbonBaseElement::OnMenuKey  
 Lo llama el marco de trabajo cuando el usuario presiona keytip menú en el panel principal.  
  
```  
virtual BOOL OnMenuKey(UINT nUpperChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nUpperChar`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método para responder cuando el usuario presiona keytip menú en el panel principal.  
  
##  <a name="a-nameonprocesskeya--cmfcribbonbaseelementonprocesskey"></a><a name="onprocesskey"></a>CMFCRibbonBaseElement::OnProcessKey  
 Lo llama el marco de trabajo cuando el usuario presiona una tecla de método abreviado.  
  
```  
virtual BOOL OnProcessKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nChar`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea que el elemento de la cinta de opciones para procesar una tecla de método abreviado.  
  
##  <a name="a-nameonrtlchangeda--cmfcribbonbaseelementonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonBaseElement::OnRTLChanged  
 Llamado por el marco de trabajo cuando el diseño cambia de dirección.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsRTL`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método para ajustar el elemento de la cinta de opciones cuando el diseño cambia de dirección. La dirección del diseño predeterminado es de izquierda a derecha.  
  
##  <a name="a-nameonsetfocusa--cmfcribbonbaseelementonsetfocus"></a><a name="onsetfocus"></a>CMFCRibbonBaseElement::OnSetFocus  
 Llamado por el marco cuando un elemento de cinta recibe o pierde el foco de entrada.  
  
```  
virtual void OnSetFocus(BOOL B);
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea que su aplicación para administrar un cambio en el foco de un elemento de la cinta de opciones.  
  
##  <a name="a-nameonshowa--cmfcribbonbaseelementonshow"></a><a name="onshow"></a>CMFCRibbonBaseElement::OnShow  
 Llamado por el marco de trabajo para mostrar u ocultar el elemento de la cinta de opciones.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método para mostrar u ocultar el elemento de la cinta de opciones.  
  
##  <a name="a-nameonshowpopupmenua--cmfcribbonbaseelementonshowpopupmenu"></a><a name="onshowpopupmenu"></a>CMFCRibbonBaseElement::OnShowPopupMenu  
 Llamado por el marco de trabajo antes de que el elemento de la cinta de opciones muestra un menú emergente.  
  
```  
virtual void OnShowPopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método notifica a la ventana primaria de la barra de la cinta de opciones que el elemento de la cinta mostrará un menú emergente.  
  
##  <a name="a-namepostmenucommanda--cmfcribbonbaseelementpostmenucommand"></a><a name="postmenucommand"></a>CMFCRibbonBaseElement::PostMenuCommand  
 Cierra el menú emergente para el elemento de la cinta de opciones y envía un mensaje de cierre al menú primario.  
  
```  
void PostMenuCommand(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 El parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 Sólo se envía el mensaje de cierre si se encuentra el elemento de la cinta de opciones en un menú emergente.  
  
##  <a name="a-nameredrawa--cmfcribbonbaseelementredraw"></a><a name="redraw"></a>CMFCRibbonBaseElement::Redraw  
 Actualiza la presentación del elemento de la cinta de opciones.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método vuelve a dibujar el rectángulo de presentación para el elemento de la cinta de opciones mediante una llamada a [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) con el `RDW_INVALIDATE`, `RDW_ERASE`, y `RDW_UPDATENOW` conjunto.  
  
##  <a name="a-namesetaccdataa--cmfcribbonbaseelementsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonBaseElement::SetACCData  
 Establece los datos de accesibilidad para el elemento de la cinta de opciones.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 La ventana principal para el elemento de la cinta de opciones.  
  
 `data`  
 Los datos de accesibilidad para el elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método establece los datos de accesibilidad para el elemento de la cinta de opciones y siempre devuelve `TRUE`. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.  
  
##  <a name="a-namesetcompactmodea--cmfcribbonbaseelementsetcompactmode"></a><a name="setcompactmode"></a>CMFCRibbonBaseElement::SetCompactMode  
 Establece el tamaño de presentación para el elemento de la cinta de opciones.  
  
```  
virtual void SetCompactMode(BOOL bCompactMode = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bCompactMode`  
 `TRUE`Para reducir el tamaño de visualización del elemento de la cinta de opciones; `FALSE` para aumentar el tamaño de visualización del elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 La siguiente tabla resume la lógica para este método.  
  
|`bCompactMode`|Tamaño actual del elemento de cinta de opciones|Nuevo tamaño de elemento de cinta de opciones|  
|--------------------|---------------------------------|-----------------------------|  
|`TRUE`|Compacto|Ningún cambio.|  
|`TRUE`|Intermedio|Compactar si es posible.|  
|`TRUE`|Grande|Nivel intermedio si es posible.|  
|`FALSE`|Compacto|Nivel intermedio si es posible; de lo contrario es grande.|  
  
##  <a name="a-namesetdataa--cmfcribbonbaseelementsetdata"></a><a name="setdata"></a>CMFCRibbonBaseElement::SetData  
 Asocia un elemento de datos con el elemento de la cinta de opciones.  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 El valor de datos.  
  
##  <a name="a-namesetdefaultmenulooka--cmfcribbonbaseelementsetdefaultmenulook"></a><a name="setdefaultmenulook"></a>CMFCRibbonBaseElement::SetDefaultMenuLook  
 Establece el elemento de la cinta de opciones para que aparezca como un comando emergente.  
  
```  
void SetDefaultMenuLook(BOOL bIsDefaultMenuLook = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsDefaultMenuLook`  
 `TRUE`Para establecer el elemento de la cinta de opciones para que aparezca como un comando emergente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdescriptiona--cmfcribbonbaseelementsetdescription"></a><a name="setdescription"></a>CMFCRibbonBaseElement::SetDescription  
 Establece la descripción del elemento de la cinta.  
  
```  
virtual void SetDescription(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 La descripción para el elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo muestra la nueva descripción en la barra de estado o en la información sobre herramientas o en el botón de menú.  
  
##  <a name="a-namesetida--cmfcribbonbaseelementsetid"></a><a name="setid"></a>CMFCRibbonBaseElement::SetID  
 Establece el identificador de comando del elemento de la cinta de opciones.  
  
```  
virtual void SetID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Identificador del comando.  
  
##  <a name="a-namesetinitialmodea--cmfcribbonbaseelementsetinitialmode"></a><a name="setinitialmode"></a>CMFCRibbonBaseElement::SetInitialMode  
 Establece el tamaño inicial del elemento de la cinta de opciones.  
  
```  
virtual void SetInitialMode(BOOL bOneRow = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bOneRow`  
 `TRUE`Para limitar el tamaño de presentación para el elemento de la cinta de opciones compactar o intermedios; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de presentación de elementos de la cinta de opciones puede ser compact, intermedio o grande.  
  
##  <a name="a-namesetkeysa--cmfcribbonbaseelementsetkeys"></a><a name="setkeys"></a>CMFCRibbonBaseElement::SetKeys  
 Establece las sugerencias de teclas para el elemento de la cinta de opciones.  
  
```  
virtual void SetKeys(
    LPCTSTR lpszKeys,  
    LPCTSTR lpszMenuKeys=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszKeys`  
 Keytip para el elemento de la cinta de opciones.  
  
 [in] `lpszMenuKeys`  
 Keytip para el menú emergente del elemento de la cinta de opciones.  
  
##  <a name="a-namesetoriginala--cmfcribbonbaseelementsetoriginal"></a><a name="setoriginal"></a>CMFCRibbonBaseElement::SetOriginal  
 Establece el elemento de la cinta original para el elemento de la cinta de opciones.  
  
```  
virtual void SetOriginal(CMFCRibbonBaseElement* pOriginal);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOriginal`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la cinta de opciones que se copian en otro contenedor conservan un puntero para el elemento de la cinta original.  
  
##  <a name="a-namesetparentcategorya--cmfcribbonbaseelementsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonBaseElement::SetParentCategory  
 Establece la categoría primaria para el elemento de la cinta de opciones.  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
 Puntero a una categoría de cinta.  
  
### <a name="remarks"></a>Comentarios  
 Los grupos con pestañas en los controles de la cinta de opciones se denominan categorías.  
  
##  <a name="a-namesetparentmenua--cmfcribbonbaseelementsetparentmenu"></a><a name="setparentmenu"></a>CMFCRibbonBaseElement::SetParentMenu  
 Establece al elemento primario de contenedor de menú para el elemento de la cinta de opciones.  
  
```  
virtual void SetParentMenu(CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuBar`  
 El menú primario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetparentribbonbara--cmfcribbonbaseelementsetparentribbonbar"></a><a name="setparentribbonbar"></a>CMFCRibbonBaseElement::SetParentRibbonBar  
 Establece la barra de cinta primario para el elemento de la cinta de opciones.  
  
```  
virtual void SetParentRibbonBar(CMFCRibbonBar* pRibbonBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRibbonBar`  
 Puntero a la barra de cinta primaria.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetrecta--cmfcribbonbaseelementsetrect"></a><a name="setrect"></a>CMFCRibbonBaseElement::SetRect  
 Establece las dimensiones del rectángulo de presentación para el elemento de la cinta de opciones.  
  
```  
void SetRect(CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Las dimensiones del rectángulo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettexta--cmfcribbonbaseelementsettext"></a><a name="settext"></a>CMFCRibbonBaseElement::SetText  
 Establece el texto y la keytip para el elemento de la cinta de opciones.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 El texto y la keytip para el elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer la keytip para el elemento de la cinta de opciones, anexar la secuencia de escape de nueva línea seguida de los caracteres de keytip a `lpszText`.  
  
### <a name="example"></a>Ejemplo  
  
```  
//Set the text for the ribbon element  
SetText(_T("Margins"))  
//Set the text and a single-letter keytip  
SetText(_T("Margins\nm"))  
//Set the text and a multiple-letter keytip  
SetText(_T("Line Numbers\nln"))  
```  
  
##  <a name="a-namesettextalwaysonrighta--cmfcribbonbaseelementsettextalwaysonright"></a><a name="settextalwaysonright"></a>CMFCRibbonBaseElement::SetTextAlwaysOnRight  
 Establece el texto del elemento de la cinta de opciones Mostrar de la derecha.  
  
```  
virtual void SetTextAlwaysOnRight(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`para mostrar el texto de la derecha; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettooltiptexta--cmfcribbonbaseelementsettooltiptext"></a><a name="settooltiptext"></a>CMFCRibbonBaseElement::SetToolTipText  
 Establece el texto de información sobre herramientas para el elemento de la cinta de opciones.  
  
```  
virtual void SetToolTipText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 El texto de información sobre herramientas.  
  
##  <a name="a-namesetvisiblea--cmfcribbonbaseelementsetvisible"></a><a name="setvisible"></a>CMFCRibbonBaseElement::SetVisible  
 Establece la visibilidad del elemento de la cinta de opciones.  
  
```  
void SetVisible(BOOL bIsVisible);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsVisible`  
 `TRUE`para mostrar el elemento de la cinta de opciones; `FALSE` para ocultar el elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestretchhorizontallya--cmfcribbonbaseelementstretchhorizontally"></a><a name="stretchhorizontally"></a>CMFCRibbonBaseElement::StretchHorizontally  
 Ajusta el ancho del elemento de la cinta de opciones.  
  
```  
virtual void StretchHorizontally();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método genera un error de aserción en compilaciones de depuración y, por tanto, no debe llamarse. Invalide este método para ajustar el ancho del elemento de la cinta de opciones.  
  
##  <a name="a-namestretchtowholerowa--cmfcribbonbaseelementstretchtowholerow"></a><a name="stretchtowholerow"></a>CMFCRibbonBaseElement::StretchToWholeRow  
 Cambia el alto del elemento de la cinta de opciones para el alto de fila especificado.  
  
```  
virtual BOOL StretchToWholeRow(
    CDC* pDC,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Este parámetro no se utiliza.  
  
 [in] `nHeight`  
 El alto de la fila.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha establecido el alto de pantalla; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para cambiar el alto del elemento de la cinta de opciones para el alto de fila especificado.  
  
##  <a name="a-nameupdatetooltipinfoa--cmfcribbonbaseelementupdatetooltipinfo"></a><a name="updatetooltipinfo"></a>CMFCRibbonBaseElement::UpdateTooltipInfo  
 Actualiza el texto de información sobre herramientas mediante el recurso de comando para el elemento de la cinta de opciones.  
  
```  
virtual void UpdateTooltipInfo();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehasfocusa--cmfcribbonbaseelementhasfocus"></a><a name="hasfocus"></a>CMFCRibbonBaseElement::HasFocus  
 Indica si el elemento primario tiene el foco de teclado.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento de la cinta se centra; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

