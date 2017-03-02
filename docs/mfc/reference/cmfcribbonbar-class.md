---
title: Clase CMFCRibbonBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonBar class
ms.assetid: a65d06fa-1a28-4cc0-8971-bc9d7c9198fe
caps.latest.revision: 41
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
ms.openlocfilehash: 48a7fbeb72257776d132785c985221b0e8148d72
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbar-class"></a>Clase CMFCRibbonBar
La clase `CMFCRibbonBar` implementa una barra de cinta similar a la que se usaba en Office 2007.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonBar::CMFCRibbonBar`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBar::ActivateContextCategory](#activatecontextcategory)|Activa una categoría de contexto que ya está visible.|  
|[CMFCRibbonBar::AddCategory](#addcategory)|Agrega una nueva categoría de cinta de opciones a la cinta.|  
|[CMFCRibbonBar::AddContextCategory](#addcontextcategory)|Agrega una categoría de contexto.|  
|[CMFCRibbonBar::AddMainCategory](#addmaincategory)|Agrega una nueva categoría principal de cinta de opciones.|  
|[CMFCRibbonBar::AddPrintPreviewCategory](#addprintpreviewcategory)||  
|[CMFCRibbonBar::AddQATOnlyCategory](#addqatonlycategory)||  
|[CMFCRibbonBar::AddToTabs](#addtotabs)|Agrega un elemento de la cinta de opciones a la derecha de una barra de cinta.|  
|[CMFCRibbonBar::CreateEx](#createex)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCRibbonBar::Create](#create)|Crea un control de barra de cinta y lo adjunta a una barra de cinta.|  
|[CMFCRibbonBar::DeactivateKeyboardFocus](#deactivatekeyboardfocus)||  
|[CMFCRibbonBar::DrawMenuImage](#drawmenuimage)||  
|[CMFCRibbonBar::DWMCompositionChanged](#dwmcompositionchanged)||  
|[CMFCRibbonBar::EnableKeyTips](#enablekeytips)|Habilita o deshabilita las sugerencias de teclas para el control de la cinta de opciones.|  
|[CMFCRibbonBar::EnablePrintPreview](#enableprintpreview)|Habilitar la **preliminar** ficha.|  
|[CMFCRibbonBar::EnableToolTips](#enabletooltips)|Habilita o deshabilita las descripciones de información sobre herramientas y la información sobre herramientas en la barra de cinta.|  
|[CMFCRibbonBar::FindByData](#findbydata)|Busca un elemento de la cinta de opciones usando los datos que un usuario especifica.|  
|[CMFCRibbonBar::FindByID](#findbyid)|Busca un elemento de la cinta de opciones que tiene el identificador de comando especificado.|  
|[CMFCRibbonBar::FindCategoryIndexByData](#findcategoryindexbydata)|Busca el índice de la categoría de la cinta que contiene los datos definidos por el usuario.|  
|[CMFCRibbonBar::ForceRecalcLayout](#forcerecalclayout)||  
|[CMFCRibbonBar::GetActiveCategory](#getactivecategory)|Obtiene un puntero a una categoría activa.|  
|[CMFCRibbonBar::GetCaptionHeight](#getcaptionheight)|Devuelve la altura del título. (Invalida [CBasePane::GetCaptionHeight](../../mfc/reference/cbasepane-class.md#getcaptionheight).)|  
|[CMFCRibbonBar::GetCategory](#getcategory)|Obtiene el puntero a una categoría ubicada en un índice especificado.|  
|[CMFCRibbonBar::GetCategoryCount](#getcategorycount)|Obtiene el número de categorías de la cinta de la barra de cinta.|  
|[CMFCRibbonBar::GetCategoryHeight](#getcategoryheight)||  
|[CMFCRibbonBar::GetCategoryIndex](#getcategoryindex)|Devuelve el índice de una categoría de la cinta.|  
|[CMFCRibbonBar::GetContextName](#getcontextname)|Recupera el título de la categoría de contexto especificada con un identificador.|  
|[CMFCRibbonBar::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonBar::GetElementsByID](#getelementsbyid)|Obtiene una matriz que contiene los punteros a todos los elementos de la cinta de opciones que tienen el identificador especificado.|  
|[CMFCRibbonBar::GetApplicationButton](#getapplicationbutton)|Obtiene un puntero a un botón de la cinta de opciones.|  
|[CMFCRibbonBar::GetFocused](#getfocused)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonBar::GetHideFlags](#gethideflags)||  
|[CMFCRibbonBar::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonBar::GetKeyboardNavigationLevel](#getkeyboardnavigationlevel)||  
|[CMFCRibbonBar::GetKeyboardNavLevelCurrent](#getkeyboardnavlevelcurrent)||  
|[CMFCRibbonBar::GetKeyboardNavLevelParent](#getkeyboardnavlevelparent)||  
|[CMFCRibbonBar::GetMainCategory](#getmaincategory)|Devuelve un puntero a la categoría de cinta de opciones seleccionada actualmente.|  
|[CMFCRibbonBar::GetQATCommandsLocation](#getqatcommandslocation)||  
|[CMFCRibbonBar::GetQATDroppedDown](#getqatdroppeddown)||  
|[CMFCRibbonBar::GetQuickAccessCommands](#getquickaccesscommands)|Rellena una lista que contiene los identificadores de comando de todos los elementos que aparecen en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::GetQuickAccessToolbarLocation](#getquickaccesstoolbarlocation)||  
|[CMFCRibbonBar::GetTabTrancateRatio](#gettabtrancateratio)||  
|[CMFCRibbonBar::GetTooltipFixedWidthLargeImage](#gettooltipfixedwidthlargeimage)||  
|[CMFCRibbonBar::GetTooltipFixedWidthRegular](#gettooltipfixedwidthregular)||  
|[CMFCRibbonBar::GetVisibleCategoryCount](#getvisiblecategorycount)||  
|[CMFCRibbonBar::HideAllContextCategories](#hideallcontextcategories)|Oculta todas las categorías que están activas y visibles.|  
|[CMFCRibbonBar::HideKeyTips](#hidekeytips)||  
|[CMFCRibbonBar::HitTest](#hittest)|Busca un puntero al elemento de la cinta de opciones que se encuentra en el punto especificado en las coordenadas de cliente de la barra de cinta.|  
|[CMFCRibbonBar::IsKeyTipEnabled](#iskeytipenabled)|Determina si se habilitan sugerencias de teclas.|  
|[CMFCRibbonBar::IsMainRibbonBar](#ismainribbonbar)||  
|[CMFCRibbonBar::IsPrintPreviewEnabled](#isprintpreviewenabled)|Determina si el **preliminar** pestaña está habilitada.|  
|[CMFCRibbonBar::IsQATEmpty](#isqatempty)||  
|[CMFCRibbonBar::IsQuickAccessToolbarOnTop](#isquickaccesstoolbarontop)|Especifica si la barra de herramientas de acceso rápido se encuentra encima de la barra de cinta.|  
|[CMFCRibbonBar::IsReplaceFrameCaption](#isreplaceframecaption)|Determina si la barra de cinta reemplaza al título del marco principal o si se agrega debajo de la leyenda del marco.|  
|[CMFCRibbonBar::IsShowGroupBorder](#isshowgroupborder)||  
|[CMFCRibbonBar::IsToolTipDescrEnabled](#istooltipdescrenabled)|Determina si las descripciones de la información sobre herramientas están habilitadas.|  
|[CMFCRibbonBar::IsToolTipEnabled](#istooltipenabled)|Determina si la información sobre herramientas de la barra de cinta está habilitada.|  
|[CMFCRibbonBar::IsTransparentCaption](#istransparentcaption)||  
|[CMFCRibbonBar::IsWindows7Look](#iswindows7look)|Indica si la cinta de opciones tiene la apariencia de Windows 7 (botón de aplicación rectangular pequeño).|  
|[CMFCRibbonBar::LoadFromResource](#loadfromresource)|Sobrecargado. Carga una barra de cinta a partir de los recursos de la aplicación.|  
|[CMFCRibbonBar::OnClickButton](#onclickbutton)||  
|[CMFCRibbonBar::OnEditContextMenu](#oneditcontextmenu)||  
|[CMFCRibbonBar::OnRTLChanged](#onrtlchanged)|(Invalida `CPane::OnRTLChanged`).|  
|[CMFCRibbonBar::OnSetAccData](#onsetaccdata)|(Invalida [CBasePane::OnSetAccData](../../mfc/reference/cbasepane-class.md#onsetaccdata).)|  
|[CMFCRibbonBar::OnShowRibbonContextMenu](#onshowribboncontextmenu)||  
|[CMFCRibbonBar::OnShowRibbonQATMenu](#onshowribbonqatmenu)||  
|[CMFCRibbonBar::OnSysKeyDown](#onsyskeydown)||  
|[CMFCRibbonBar::OnSysKeyUp](#onsyskeyup)||  
|[CMFCRibbonBar::PopTooltip](#poptooltip)||  
|[CMFCRibbonBar::PreTranslateMessage](#pretranslatemessage)|(Invalida `CBasePane::PreTranslateMessage`).|  
|[CMFCRibbonBar::RecalcLayout](#recalclayout)|(Invalida [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CMFCRibbonBar::RemoveAllCategories](#removeallcategories)|Quita todas las categorías de la cinta de opciones de la barra de cinta.|  
|[CMFCRibbonBar::RemoveAllFromTabs](#removeallfromtabs)|Quita todos los elementos de la cinta de opciones del área de pestañas.|  
|[CMFCRibbonBar::RemoveCategory](#removecategory)|Quita la categoría de cinta de opciones que se encuentra en el índice especificado.|  
|[CMFCRibbonBar::SaveToXMLBuffer](#savetoxmlbuffer)|Guarda la barra de cinta en un búfer.|  
|[CMFCRibbonBar::SaveToXMLFile](#savetoxmlfile)|Guarda la barra de cinta en un archivo XML.|  
|[CMFCRibbonBar::SetActiveCategory](#setactivecategory)|Establece una categoría especificada de la cinta de opciones como activa.|  
|[CMFCRibbonBar::SetActiveMDIChild](#setactivemdichild)||  
|[CMFCRibbonBar::SetElementKeys](#setelementkeys)|Establece las sugerencias de teclas especificadas para todos los elementos de la cinta de opciones que tienen el identificador de comando especificado.|  
|[CMFCRibbonBar::SetApplicationButton](#setapplicationbutton)|Asigna un botón de la cinta de opciones de aplicación a la barra de cinta.|  
|[CMFCRibbonBar::SetKeyboardNavigationLevel](#setkeyboardnavigationlevel)||  
|[CMFCRibbonBar::SetMaximizeMode](#setmaximizemode)||  
|[CMFCRibbonBar::SetQuickAccessCommands](#setquickaccesscommands)|Agrega uno o más elementos de la cinta de opciones a la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::SetQuickAccessDefaultState](#setquickaccessdefaultstate)|Especifica el estado predeterminado de la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::SetQuickAccessToolbarOnTop](#setquickaccesstoolbarontop)|Coloca la barra de herramientas de acceso rápido (QAT) encima o debajo de la barra de cinta.|  
|[CMFCRibbonBar::SetTooltipFixedWidth](#settooltipfixedwidth)||  
|[CMFCRibbonBar::SetWindows7Look](#setwindows7look)|Habilita/deshabilita la apariencia de Windows 7 (botón de aplicación rectangular pequeño) para la cinta de opciones.|  
|[CMFCRibbonBar::ShowCategory](#showcategory)|Muestra u oculta la categoría de la cinta de opciones especificada.|  
|[CMFCRibbonBar::ShowContextCategories](#showcontextcategories)|Muestra u oculta las categorías de contexto que tienen el identificador especificado.|  
|[CMFCRibbonBar::ShowKeyTips](#showkeytips)||  
|[CMFCRibbonBar::ToggleMimimizeState](#togglemimimizestate)|Alterna la barra de cinta entre los estados minimizado y maximizado.|  
|[CMFCRibbonBar::TranslateChar](#translatechar)||  
  
## <a name="remarks"></a>Comentarios  
 Microsoft presentó la cinta de opciones de Office Fluent junto con el lanzamiento de Microsoft Office 2007. Esta barra de cinta es mucho más que un control nuevo: representa un nuevo paradigma de interfaz de usuario. La cinta de opciones es un panel que contiene un conjunto de pestañas denominada categorías. Cada categoría se divide lógicamente en paneles de cinta y cada panel puede contener varios controles y botones de comando.  
  
 Los elementos que aparecen en la barra de cinta se expanden y se contrae para optimizar el espacio disponible. Por ejemplo, si un panel de cinta no tiene suficiente espacio para mostrar sus elementos, se convierte en un botón de menú que muestra los subelementos en un menú emergente. La barra de cinta se comporta como una barra de control estática (no flotante) y se puede acoplar en la parte superior de un marco.  
  
 Puede usar la clase `CMFCRibbonStatusBar` para implementar una barra de estado similar a la que se usaba en Office 2007. Una categoría de cinta contiene (y muestra) en un grupo de [paneles de la cinta de opciones](../../mfc/reference/cmfcribbonpanel-class.md). Cada panel de la cinta de opciones contiene uno o varios elementos de cinta de opciones, que se derivan de [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 Para obtener información sobre cómo agregar una barra de cinta a una aplicación MFC existente, vea [Tutorial: actualizar la aplicación Scribble de MFC](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonbar.h  
  
##  <a name="a-nameactivatecontextcategorya--cmfcribbonbaractivatecontextcategory"></a><a name="activatecontextcategory"></a>CMFCRibbonBar::ActivateContextCategory  
 Activa una categoría de contexto que ya está visible.  
  
```  
BOOL ActivateContextCategory(UINT uiContextID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiContextID`  
 El identificador de categoría de contexto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si una categoría de contexto con `uiContextID` se encuentra y activado; en caso contrario, `FALSE`.  
  
##  <a name="a-nameaddcategorya--cmfcribbonbaraddcategory"></a><a name="addcategory"></a>CMFCRibbonBar::AddCategory  
 Crea e inicializa una nueva categoría de cinta de opciones de la barra de la cinta de opciones.  
  
```  
CMFCRibbonCategory* AddCategory(
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage= CSize(16,
    16),  
    CSize sizeLargeImage= CSize(32,
    32),  
    int nInsertAt = -1,  
    CRuntimeClass* pRTI= NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Nombre de la categoría de cinta de opciones.  
  
 [in] `uiSmallImagesResID`  
 Identificador de recurso de la lista de imágenes pequeñas de la categoría de cinta de opciones.  
  
 [in] `uiLargeImagesResID`  
 Identificador de recurso de la lista de imágenes de gran tamaño para la categoría de cinta de opciones.  
  
 [in] `sizeSmallImage`  
 Especifica el tamaño de las imágenes pequeñas de la categoría de cinta de opciones.  
  
 [in] `sizeLargeImage`  
 Especifica el tamaño de imágenes de gran tamaño para la categoría de cinta de opciones.  
  
 [in] `nInsertAt`  
 Índice de base cero de la ubicación de la categoría.  
  
 [in] `pRTI`  
 Puntero a un [CMFCRibbonCategory clase](../../mfc/reference/cmfcribboncategory-class.md) clase en tiempo de ejecución para crear dinámicamente una categoría de cinta de opciones en tiempo de ejecución.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la nueva categoría de cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si el `pRTI` parámetro no es `NULL`, la nueva categoría de cinta de opciones se crea dinámicamente mediante la clase en tiempo de ejecución.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `AddCategory` método en la `CMFCRibbonBar` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#5;](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_1.cpp)]  
  
##  <a name="a-nameaddcontextcategorya--cmfcribbonbaraddcontextcategory"></a><a name="addcontextcategory"></a>CMFCRibbonBar::AddContextCategory  
 Crea e inicializa una nueva categoría de contexto para la barra de cinta.  
  
```  
CMFCRibbonCategory* AddContextCategory(
    LPCTSTR lpszName,  
    LPCTSTR lpszContextName,  
    UINT uiContextID,  
    AFX_RibbonCategoryColor clrContext,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32),  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Nombre de la categoría.  
  
 [in] `lpszContextName`  
 Nombre del título de categoría de contexto.  
  
 [in] `uiContextID`  
 Identificador de contexto.  
  
 [in] `clrContext`  
 Color del título de categoría de contexto.  
  
 [in] `uiSmallImagesResID`  
 Identificador de recurso de la imagen pequeña de una categoría de contexto.  
  
 [in] `uiLargeImagesResID`  
 Identificador de recurso de la imagen grande de una categoría de contexto.  
  
 [in] `sizeSmallImage`  
 Tamaño de una imagen pequeña.  
  
 [in] `sizeLargeImage`  
 Tamaño de una imagen grande.  
  
 [in] `pRTI`  
 Puntero a una clase en tiempo de ejecución.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la categoría recién creada, o `NULL` si la `CreateObject` método `pRTI` no se puede crear la categoría especificada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para agregar una categoría de contexto. Categorías de contexto son un tipo especial de categoría que se puede mostrar u ocultar en tiempo de ejecución, dependiendo del contexto de aplicación actual. Por ejemplo, cuando el usuario selecciona un objeto, puede mostrar fichas especiales con categorías de contexto que se utiliza para cambiar el objeto seleccionado específico.  
  
 El color de una categoría de contexto puede ser uno de los siguientes valores:  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="a-nameaddmaincategorya--cmfcribbonbaraddmaincategory"></a><a name="addmaincategory"></a>CMFCRibbonBar::AddMainCategory  
 Crea una nueva categoría principal de la cinta de opciones de la barra de la cinta de opciones.  
  
```  
CMFCRibbonMainPanel* AddMainCategory(
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Nombre de la categoría principal de la cinta de opciones.  
  
 [in] `uiSmallImagesResID`  
 Identificador de recurso de imágenes pequeñas.  
  
 [in] `uiLargeImagesResID`  
 Identificador de recurso de imágenes de gran tamaño.  
  
 [in] `sizeSmallImage`  
 El tamaño de las imágenes pequeñas.  
  
 [in] `sizeLargeImage`  
 El tamaño de imágenes de gran tamaño.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la nueva categoría principal de la cinta de opciones si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si ya existe una categoría principal de la cinta de opciones, se elimina.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `AddMainCategory` método en la `CMFCRibbonBar` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&4;](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_2.cpp)]  
  
##  <a name="a-nameaddprintpreviewcategorya--cmfcribbonbaraddprintpreviewcategory"></a><a name="addprintpreviewcategory"></a>CMFCRibbonBar::AddPrintPreviewCategory  
 Crea una categoría de la vista previa de impresión en la barra de la cinta de opciones.  
  
```  
CMFCRibbonCategory* AddPrintPreviewCategory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la nueva categoría de cinta si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una categoría de cinta y los controles que necesita para proporcionar una vista previa de impresión.  
  
##  <a name="a-nameaddqatonlycategorya--cmfcribbonbaraddqatonlycategory"></a><a name="addqatonlycategory"></a>CMFCRibbonBar::AddQATOnlyCategory  
 Crea una categoría de cinta de opciones de barra de herramientas de acceso rápido.  
  
```  
CMFCRibbonCategory* AddQATOnlyCategory(
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 Nombre de la categoría.  
  
 [in] `uiSmallImagesResID`  
 Identificador de recurso de la lista de imágenes para la categoría.  
  
 [in] `sizeSmallImage`  
 Tamaño de imágenes para los elementos de la cinta de opciones en la categoría.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la nueva categoría si el método se realizó correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 La categoría de cinta de opciones de barra de herramientas de acceso rápido sólo se utiliza en el cuadro de diálogo de personalización de barra de herramientas de acceso rápido.  
  
##  <a name="a-nameaddtotabsa--cmfcribbonbaraddtotabs"></a><a name="addtotabs"></a>CMFCRibbonBar::AddToTabs  
 Agrega el elemento especificado de la cinta de opciones a la fila de pestañas de la barra de la cinta de opciones.  
  
```  
void AddToTabs(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pElement`  
 Puntero a un elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El elemento de la cinta se coloca antes de los botones del sistema.  
  
##  <a name="a-namecmfcribbonbara--cmfcribbonbarcmfcribbonbar"></a><a name="cmfcribbonbar"></a>CMFCRibbonBar::CMFCRibbonBar  
 Construye e inicializa un [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) objeto.  
  
```  
CMFCRibbonBar(BOOL bReplaceFrameCaption = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bReplaceFrameCaption`  
 `TRUE`de la barra de la cinta de opciones reemplazar el título de la ventana de marco principal; `FALSE` para buscar la barra de cinta en el título de la ventana de marco principal.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreatea--cmfcribbonbarcreate"></a><a name="create"></a>CMFCRibbonBar::Create  
 Crea una ventana de la barra de la cinta de opciones.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_RIBBON_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Puntero a la ventana primaria de la barra de la cinta de opciones.  
  
 [in] `dwStyle`  
 Combinación lógica de estilos de la nueva ventana.  
  
 [in] `nID`  
 Id. de la nueva ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se creó la ventana; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CMFCRibbonBar` clase.  
  
 [!code-cpp[1 NVC_MFC_RibbonApp](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_3.cpp)]  
  
##  <a name="a-namecreateexa--cmfcribbonbarcreateex"></a><a name="createex"></a>CMFCRibbonBar::CreateEx  
 Crea una ventana de la barra de la cinta de opciones.  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_RIBBON_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Puntero a la ventana primaria de la barra de la cinta de opciones.  
  
 [in] `dwCtrlStyle`  
 Este parámetro no se utiliza.  
  
 [in] `dwStyle`  
 Combinación lógica de estilos de la nueva ventana.  
  
 [in] `nID`  
 Id. de la nueva ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se creó la ventana; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedeactivatekeyboardfocusa--cmfcribbonbardeactivatekeyboardfocus"></a><a name="deactivatekeyboardfocus"></a>CMFCRibbonBar::DeactivateKeyboardFocus  
 Cierra todos los controles de keytip en la barra de la cinta de opciones.  
  
```  
void DeactivateKeyboardFocus(BOOL bSetFocus = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSetFocus`  
 `TRUE`Para establecer el foco a la ventana primaria de la barra de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawmenuimagea--cmfcribbonbardrawmenuimage"></a><a name="drawmenuimage"></a>CMFCRibbonBar::DrawMenuImage  
 Dibuja la imagen de un botón de menú.  
  
```  
BOOL DrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuItem,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el botón de menú.  
  
 [in] `pMenuItem`  
 Puntero a un botón de menú de la barra de herramientas.  
  
 [in] `rectImage`  
 El rectángulo de presentación para un botón de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen se dibuja; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedwmcompositionchangeda--cmfcribbonbardwmcompositionchanged"></a><a name="dwmcompositionchanged"></a>CMFCRibbonBar::DWMCompositionChanged  
 Ajusta la presentación de la barra de cinta cuando la composición del Administrador de ventanas de escritorio (DWM) está habilitada o deshabilitada.  
  
```  
virtual void DWMCompositionChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablekeytipsa--cmfcribbonbarenablekeytips"></a><a name="enablekeytips"></a>CMFCRibbonBar::EnableKeyTips  
 Habilita o deshabilita la característica de keytip para la barra de cinta.  
  
```  
void EnableKeyTips(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la característica de sugerencias de teclas; `FALSE` para deshabilitar la característica de sugerencias de teclas.  
  
### <a name="remarks"></a>Comentarios  
 Al habilitar esta característica, sugerencias de teclas se muestran cuando el usuario presiona el botón ALT o F10. Cuando el usuario presiona la tecla ALT, sugerencias de teclas se muestran con un retraso de 200 milisegundos. Este retraso permite accesos directos a ejecutarse de forma que la tecla ALT presionada no interfiere con otras combinaciones que incluyen la tecla ALT.  
  
##  <a name="a-nameenableprintpreviewa--cmfcribbonbarenableprintpreview"></a><a name="enableprintpreview"></a>CMFCRibbonBar::EnablePrintPreview  
 Habilita o deshabilita la **preliminar** característica.  
  
```  
void EnablePrintPreview(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la **preliminar** característica; `FALSE` para deshabilitar la **preliminar** característica.  
  
### <a name="remarks"></a>Comentarios  
 Si `bEnable` es `FALSE` y existe una categoría de la vista previa de impresión, se elimina.  
  
 De forma predeterminada el **preliminar** característica está habilitada.  
  
##  <a name="a-nameenabletooltipsa--cmfcribbonbarenabletooltips"></a><a name="enabletooltips"></a>CMFCRibbonBar::EnableToolTips  
 Habilita o deshabilita la información sobre herramientas y las descripciones de la información sobre herramientas opcional en la barra de la cinta de opciones.  
  
```  
void EnableToolTips(
    BOOL bEnable = TRUE,  
    BOOL bEnableDescr = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la información sobre herramientas en la barra de la cinta de opciones. `FALSE` para deshabilitar la información sobre herramientas en la barra de la cinta de opciones.  
  
 [in] `bEnableDescr`  
 `TRUE`Para habilitar las descripciones de la información sobre herramientas en la información sobre herramientas; `FALSE` para deshabilitar las descripciones de la información sobre herramientas en la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El `bEnable` parámetro determina si se muestra información sobre herramientas cuando se sitúa el mouse sobre un elemento de la cinta de opciones. El `bEnableDescr` parámetro determina si el texto descriptivo adicional aparece con el texto de información sobre herramientas.  
  
##  <a name="a-namefindbydataa--cmfcribbonbarfindbydata"></a><a name="findbydata"></a>CMFCRibbonBar::FindByData  
 Recupera un puntero a un elemento de cinta si tiene los datos especificados y la visibilidad.  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Los datos asociados a un elemento de la cinta de opciones.  
  
 [in] `bVisibleOnly`  
 `TRUE`para buscar los elementos visibles de la cinta de opciones `FALSE` para buscar todos los elementos de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento de la cinta si tiene los datos especificados y la visibilidad; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Un elemento de cinta es cualquier control que puede agregar a la cinta de opciones, como un botón de la cinta de opciones, o una categoría de cinta o un control deslizante de la cinta de opciones.  
  
##  <a name="a-namefindbyida--cmfcribbonbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonBar::FindByID  
 Recupera un puntero al elemento de cinta de opciones con los valores de identificador y búsqueda de comando especificado.  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE,  
    BOOL bExcludeQAT = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Identificador de comando para un elemento de la cinta de opciones.  
  
 [in] `bVisibleOnly`  
 `TRUE`para buscar los elementos visibles de la cinta de opciones `FALSE` para buscar todos los elementos de la cinta de opciones.  
  
 [in] `bExcludeQAT`  
 `TRUE`excluir elementos de la barra de herramientas de acceso rápido de la búsqueda; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento de la cinta si tiene los valores de identificador y búsqueda de comando especificado; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Un elemento de cinta es cualquier control de cinta de opciones que se puede agregar a la cinta de opciones, como un botón de la cinta de opciones, o una categoría de cinta o un control deslizante de la cinta de opciones.  
  
 En general, puede haber más de un elemento de la cinta de opciones que tiene el mismo identificador de comando. Si desea obtener punteros a todos los elementos de la cinta de opciones que usan un identificador de comando especificado, use la [CMFCRibbonBar::GetElementsByID](#getelementsbyid) método.  
  
##  <a name="a-namefindcategoryindexbydataa--cmfcribbonbarfindcategoryindexbydata"></a><a name="findcategoryindexbydata"></a>CMFCRibbonBar::FindCategoryIndexByData  
 Recupera el índice de la categoría de cinta que contiene los datos especificados.  
  
```  
int FindCategoryIndexByData(DWORD dwData) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Los datos asociados a una categoría de cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de una categoría de cinta si el método se realizó correctamente; de lo contrario, devuelve-1.  
  
##  <a name="a-nameforcerecalclayouta--cmfcribbonbarforcerecalclayout"></a><a name="forcerecalclayout"></a>CMFCRibbonBar::ForceRecalcLayout  
 Ajusta el diseño de todos los elementos en la barra de la cinta y la ventana primaria y vuelve a dibujar toda la ventana.  
  
```  
void ForceRecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetactivecategorya--cmfcribbonbargetactivecategory"></a><a name="getactivecategory"></a>CMFCRibbonBar::GetActiveCategory  
 Recupera un puntero a la categoría de activo de la cinta de opciones.  
  
```  
CMFCRibbonCategory* GetActiveCategory() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la categoría de activo de la cinta de opciones; o `NULL` si ninguna categoría está activa.  
  
### <a name="remarks"></a>Comentarios  
 Una categoría es activa si tiene el foco. De forma predeterminada, la categoría activa es la primera categoría en el lado izquierdo de la barra de la cinta de opciones.  
  
 La categoría principal se muestra cuando el usuario presiona el botón de la aplicación y no puede ser la misma.  
  
##  <a name="a-namegetapplicationbuttona--cmfcribbonbargetapplicationbutton"></a><a name="getapplicationbutton"></a>CMFCRibbonBar::GetApplicationButton  
 Recupera un puntero al botón aplicación.  
  
```  
CMFCRibbonApplicationButton* GetApplicationButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al botón de la aplicación; o `NULL` si no se ha establecido el botón.  
  
##  <a name="a-namegetcaptionheighta--cmfcribbonbargetcaptionheight"></a><a name="getcaptionheight"></a>CMFCRibbonBar::GetCaptionHeight  
 Recupera el alto del área de título de la barra de la cinta de opciones.  
  
```  
int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, del área de título de la barra de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcategorya--cmfcribbonbargetcategory"></a><a name="getcategory"></a>CMFCRibbonBar::GetCategory  
 Recupera un puntero a la categoría de cinta de opciones en el índice especificado.  
  
```  
CMFCRibbonCategory* GetCategory(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero de una categoría de cinta de opciones en la lista de categorías de la cinta de opciones que se encuentra en la barra de cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la categoría de cinta de opciones en el índice especificado; de lo contrario, `NULL` si `nIndex` estaba fuera del intervalo.  
  
##  <a name="a-namegetcategorycounta--cmfcribbonbargetcategorycount"></a><a name="getcategorycount"></a>CMFCRibbonBar::GetCategoryCount  
 Recupera el número de categorías de la cinta de opciones en la barra de la cinta de opciones.  
  
```  
int GetCategoryCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de las categorías de la cinta de opciones en la barra de la cinta de opciones.  
  
##  <a name="a-namegetcategoryheighta--cmfcribbonbargetcategoryheight"></a><a name="getcategoryheight"></a>CMFCRibbonBar::GetCategoryHeight  
 Recupera el alto de la categoría.  
  
```  
int GetCategoryHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de la categoría.  
  
### <a name="remarks"></a>Comentarios  
 El alto de la categoría incluye el alto de la pestaña de categoría.  
  
##  <a name="a-namegetcategoryindexa--cmfcribbonbargetcategoryindex"></a><a name="getcategoryindex"></a>CMFCRibbonBar::GetCategoryIndex  
 Recupera el índice de la categoría especificada de la cinta de opciones.  
  
```  
int GetCategoryIndex(CMFCRibbonCategory* pCategory) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCategory`  
 Puntero a una categoría de cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de una categoría de cinta especificado por `pCategory`; o -1 si no se encuentra la categoría de cinta de opciones.  
  
##  <a name="a-namegetcontextnamea--cmfcribbonbargetcontextname"></a><a name="getcontextname"></a>CMFCRibbonBar::GetContextName  
 Recupera el nombre del título de categoría de contexto especificado por un identificador de contexto.  
  
```  
BOOL GetContextName(
    UINT uiContextID,  
    CString& strName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiContextID`  
 Un identificador de contexto de categoría de cinta de opciones.  
  
 [out] `strName`  
 El nombre de un título de categoría de contexto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE` si `uiContextID` es cero o no se encontró el título de la categoría de contexto.  
  
##  <a name="a-namegetdroppeddowna--cmfcribbonbargetdroppeddown"></a><a name="getdroppeddown"></a>CMFCRibbonBar::GetDroppedDown  
 Recupera el elemento de la cinta de opciones que actualmente está desplegado.  
  
```  
virtual CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento de la cinta de opciones que se encuentra actualmente o `NULL` si ningún elemento de la cinta se encuentra actualmente hacia abajo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetelementsbyida--cmfcribbonbargetelementsbyid"></a><a name="getelementsbyid"></a>CMFCRibbonBar::GetElementsByID  
 Recupera una matriz de punteros a todos los elementos de la cinta de opciones que tienen un Id.  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& arButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Id. de comando de un elemento de la cinta de opciones.  
  
 [out] `arButtons`  
 Matriz de punteros a elementos de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Varios elementos de la cinta de opciones pueden tener el mismo identificador de comando ya se pueden copiar algunos elementos de la cinta de opciones en la barra de herramientas de acceso rápido.  
  
##  <a name="a-namegethideflagsa--cmfcribbonbargethideflags"></a><a name="gethideflags"></a>CMFCRibbonBar::GetHideFlags  
 Recupera las marcas que indican la cantidad de la barra de la cinta de opciones está visible.  
  
```  
DWORD GetHideFlags() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las marcas que indican la cantidad de la barra de la cinta de opciones está visible.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumera las combinaciones posibles de marcas para el valor devuelto:  
  
 `AFX_RIBBONBAR_HIDE_ELEMENTS`  
 La barra de cinta está minimizada vertical y las fichas de categoría, botón principal y barra de herramientas de acceso rápido son visibles.  
  
 `AFX_RIBBONBAR_HIDE_ALL`  
 El ancho de la barra de cinta es menor que el ancho mínimo y está completamente oculta.  
  
##  <a name="a-namegetitemidslista--cmfcribbonbargetitemidslist"></a><a name="getitemidslist"></a>CMFCRibbonBar::GetItemIDsList  
 Recupera los identificadores de comando para la colección de elementos de la cinta de opciones en la barra de cinta especificada.  
  
```  
void GetItemIDsList(CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lstItems`  
 La lista de identificadores de comando para los elementos de cinta de opciones que se encuentran en la barra de cinta.  
  
 [in] `bHiddenOnly`  
 `TRUE`Para excluir elementos de la cinta de opciones que se muestran; `FALSE` para incluir todos los elementos de la cinta de opciones en la barra de cinta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetkeyboardnavigationlevela--cmfcribbonbargetkeyboardnavigationlevel"></a><a name="getkeyboardnavigationlevel"></a>CMFCRibbonBar::GetKeyboardNavigationLevel  
 Recupera el nivel de navegación actual cuando el usuario presiona las sugerencias de teclas que se encuentran en la barra de cinta.  
  
```  
int GetKeyboardNavigationLevel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nivel de navegación actual que el usuario presiona las sugerencias de teclas que se encuentran en la barra de cinta. En la tabla siguiente enumera los posibles valores devueltos:  
  
 -1  
 No se muestran las sugerencias de teclas.  
  
 0  
 Se muestran las sugerencias de teclas.  
  
 1  
 Usuario ha presionado keytip mostrada.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetkeyboardnavlevelcurrenta--cmfcribbonbargetkeyboardnavlevelcurrent"></a><a name="getkeyboardnavlevelcurrent"></a>CMFCRibbonBar::GetKeyboardNavLevelCurrent  
 Recupera el objeto actual de exploración de teclado en la barra de la cinta de opciones.  
  
```  
CObject* GetKeyboardNavLevelCurrent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto actual de exploración de teclado en la barra de la cinta de opciones. de lo contrario `NULL` si no hay ningún objeto actualmente muestra información sobre las teclas.  
  
### <a name="remarks"></a>Comentarios  
 El objeto que está mostrando información sobre las teclas es el objeto de navegación de teclado actual.  
  
##  <a name="a-namegetkeyboardnavlevelparenta--cmfcribbonbargetkeyboardnavlevelparent"></a><a name="getkeyboardnavlevelparent"></a>CMFCRibbonBar::GetKeyboardNavLevelParent  
 Recupera el objeto de navegación de teclado primario en la barra de la cinta de opciones.  
  
```  
CObject* GetKeyboardNavLevelParent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de navegación de teclado primario en la barra de la cinta de opciones. de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario presiona keytip en la barra de la cinta de opciones, el objeto de navegación de teclado actual se convierte en el objeto de navegación de teclado primario.  
  
##  <a name="a-namegetmaincategorya--cmfcribbonbargetmaincategory"></a><a name="getmaincategory"></a>CMFCRibbonBar::GetMainCategory  
 Recupera un puntero a la categoría principal de la cinta de opciones.  
  
```  
CMFCRibbonCategory* GetMainCategory() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la categoría principal de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 La categoría principal de la cinta de opciones contiene el panel principal de la cinta de opciones.  
  
##  <a name="a-namegetqatcommandslocationa--cmfcribbonbargetqatcommandslocation"></a><a name="getqatcommandslocation"></a>CMFCRibbonBar::GetQATCommandsLocation  
 Recupera el rectángulo de presentación de la sección de comandos de la barra de herramientas de acceso rápido.  
  
```  
CRect GetQATCommandsLocation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo de presentación de la sección de comandos de la barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
 La sección de comandos del rectángulo de presentación no incluye el botón de personalización.  
  
##  <a name="a-namegetqatdroppeddowna--cmfcribbonbargetqatdroppeddown"></a><a name="getqatdroppeddown"></a>CMFCRibbonBar::GetQATDroppedDown  
 Recupera un puntero al elemento de cinta de opciones en la barra de herramientas de acceso rápido que tiene el menú emergente desplegado.  
  
```  
CMFCRibbonBaseElement* GetQATDroppedDown();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta de opciones en la barra de herramientas de acceso rápido que tiene el menú emergente desplegado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetquickaccesscommandsa--cmfcribbonbargetquickaccesscommands"></a><a name="getquickaccesscommands"></a>CMFCRibbonBar::GetQuickAccessCommands  
 Recupera una lista de identificadores de comando para los elementos de la cinta de opciones en la barra de herramientas de acceso rápido.  
  
```  
void GetQuickAccessCommands(CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lstCommands`  
 La lista de identificadores de comando para los elementos de la cinta de opciones en la barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
 La lista no contiene elementos de cinta son separadores de control.  
  
##  <a name="a-namegetquickaccesstoolbarlocationa--cmfcribbonbargetquickaccesstoolbarlocation"></a><a name="getquickaccesstoolbarlocation"></a>CMFCRibbonBar::GetQuickAccessToolbarLocation  
 Recupera el rectángulo de presentación de la barra de herramientas de acceso rápido.  
  
```  
CRect GetQuickAccessToolbarLocation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo de presentación de la barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabtrancateratioa--cmfcribbonbargettabtrancateratio"></a><a name="gettabtrancateratio"></a>CMFCRibbonBar::GetTabTrancateRatio  
 Recupera la reducción de tamaño porcentual en el ancho de las fichas de categoría.  
  
```  
int GetTabTrancateRatio() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El porcentaje de tamaño de reducción en el ancho de las fichas de categoría.  
  
### <a name="remarks"></a>Comentarios  
 Fichas de categorías se reducen el ancho cuando no hay suficiente ancho de la barra de la cinta de opciones.  
  
##  <a name="a-namegettooltipfixedwidthlargeimagea--cmfcribbonbargettooltipfixedwidthlargeimage"></a><a name="gettooltipfixedwidthlargeimage"></a>CMFCRibbonBar::GetTooltipFixedWidthLargeImage  
 Recupera el tamaño del ancho de la información sobre herramientas de la barra de la cinta de opciones.  
  
```  
int GetTooltipFixedWidthLargeImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El gran tamaño de la información sobre herramientas ancho en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del ancho de la información sobre herramientas es 0, varía según el ancho.  
  
##  <a name="a-namegettooltipfixedwidthregulara--cmfcribbonbargettooltipfixedwidthregular"></a><a name="gettooltipfixedwidthregular"></a>CMFCRibbonBar::GetTooltipFixedWidthRegular  
 Recupera el tamaño normal del ancho de la información sobre herramientas de la barra de la cinta de opciones.  
  
```  
int GetTooltipFixedWidthRegular() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño normal de información sobre herramientas ancho en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño normal del ancho de la información sobre herramientas es 0, varía según el ancho.  
  
##  <a name="a-namegetvisiblecategorycounta--cmfcribbonbargetvisiblecategorycount"></a><a name="getvisiblecategorycount"></a>CMFCRibbonBar::GetVisibleCategoryCount  
 Recupera el número de categorías visibles en la barra de la cinta de opciones.  
  
```  
int GetVisibleCategoryCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de categorías visibles en la barra de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehideallcontextcategoriesa--cmfcribbonbarhideallcontextcategories"></a><a name="hideallcontextcategories"></a>CMFCRibbonBar::HideAllContextCategories  
 Oculta todas las categorías de contexto en la barra de la cinta de opciones.  
  
```  
BOOL HideAllContextCategories();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se oculta la categoría de al menos un contexto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si una categoría de contexto está activa, la categoría activa se restablece a la primera categoría visible en la lista de categorías.  
  
##  <a name="a-namehidekeytipsa--cmfcribbonbarhidekeytips"></a><a name="hidekeytips"></a>CMFCRibbonBar::HideKeyTips  
 Oculta todas las sugerencias de teclas en la barra de la cinta de opciones.  
  
```  
void HideKeyTips();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehittesta--cmfcribbonbarhittest"></a><a name="hittest"></a>CMFCRibbonBar::HitTest  
 Recupera un puntero al elemento de cinta especificado por la ubicación del punto.  
  
```  
virtual CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckActiveCategory= FALSE,  
    BOOL bCheckPanelCaption= FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Ubicación del punto en coordenadas de la barra de cinta de opciones.  
  
 [in] `bCheckActiveCategory`  
 `TRUE`para buscar la categoría activa; `FALSE` no para buscar la categoría activa.  
  
 [in] `bCheckPanelCaption`  
 `TRUE`Para probar el título del panel de la cinta con el punto que se encuentra en él; `FALSE` no para probar el título del panel de la cinta con el punto ubicado en ella. Vea la sección Comentarios para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de cinta que se encuentra en el punto especificado; de lo contrario `NULL` si el punto no se encuentra en un elemento de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 No se ha probado el título del panel de la cinta con el punto ubicado en él, a menos que la `bCheckActiveCategory` parámetro es `TRUE`.  
  
##  <a name="a-nameiskeytipenableda--cmfcribbonbariskeytipenabled"></a><a name="iskeytipenabled"></a>CMFCRibbonBar::IsKeyTipEnabled  
 Indica si está habilitada la característica de sugerencias de teclas.  
  
```  
BOOL IsKeyTipEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la característica de sugerencias de teclas; de lo contrario, `FALSE`.  
  
##  <a name="a-nameismainribbonbara--cmfcribbonbarismainribbonbar"></a><a name="ismainribbonbar"></a>CMFCRibbonBar::IsMainRibbonBar  
 Indica si la barra de cinta es la barra de cinta principal.  
  
```  
virtual BOOL IsMainRibbonBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `TRUE`. Invalide este método para indicar si la barra de cinta es la barra de cinta principal.  
  
##  <a name="a-nameisprintpreviewenableda--cmfcribbonbarisprintpreviewenabled"></a><a name="isprintpreviewenabled"></a>CMFCRibbonBar::IsPrintPreviewEnabled  
 Indica si la **preliminar** característica está habilitada.  
  
```  
BOOL IsPrintPreviewEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el **preliminar** característica está habilitada; en caso contrario, `FALSE`.  
  
##  <a name="a-nameisqatemptya--cmfcribbonbarisqatempty"></a><a name="isqatempty"></a>CMFCRibbonBar::IsQATEmpty  
 Indica si la barra de herramientas de acceso rápido contiene botones de comando.  
  
```  
BOOL IsQATEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas de acceso rápido contiene botones de comando; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisquickaccesstoolbarontopa--cmfcribbonbarisquickaccesstoolbarontop"></a><a name="isquickaccesstoolbarontop"></a>CMFCRibbonBar::IsQuickAccessToolbarOnTop  
 Indica si la barra de herramientas de acceso rápido se encuentra en o debajo de la barra de la cinta de opciones.  
  
```  
BOOL IsQuickAccessToolbarOnTop() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas de acceso rápido se encuentra sobre la barra de la cinta de opciones. `FALSE` si la barra de herramientas de acceso rápido se encuentra en la barra de cinta.  
  
##  <a name="a-nameisreplaceframecaptiona--cmfcribbonbarisreplaceframecaption"></a><a name="isreplaceframecaption"></a>CMFCRibbonBar::IsReplaceFrameCaption  
 Indica si la barra de cinta reemplaza o está bajo el título de la ventana de marco principal.  
  
```  
BOOL IsReplaceFrameCaption() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de cinta reemplaza el título de la ventana de marco principal; `FALSE` si la barra de cinta está bajo el título de la ventana de marco principal.  
  
##  <a name="a-nameisshowgroupbordera--cmfcribbonbarisshowgroupborder"></a><a name="isshowgroupborder"></a>CMFCRibbonBar::IsShowGroupBorder  
 Indica si los grupos de botones de la barra de la cinta de opciones muestran un borde de grupo.  
  
```  
virtual BOOL IsShowGroupBorder(CMFCRibbonButtonsGroup* pGroup) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pGroup`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método siempre devuelve `FALSE`. Invalide este método para indicar si un borde de grupo muestran los grupos de botones de la barra de la cinta de opciones.  
  
##  <a name="a-nameistooltipdescrenableda--cmfcribbonbaristooltipdescrenabled"></a><a name="istooltipdescrenabled"></a>CMFCRibbonBar::IsToolTipDescrEnabled  
 Indica si se habilitan las descripciones de la información sobre herramientas.  
  
```  
BOOL IsToolTipDescrEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se habilitan las descripciones de la información sobre herramientas; `FALSE` si se deshabilitan las descripciones de la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Las descripciones de la información sobre herramientas son texto descriptivo adicional que se muestran con el texto de información sobre herramientas.  
  
##  <a name="a-nameistooltipenableda--cmfcribbonbaristooltipenabled"></a><a name="istooltipenabled"></a>CMFCRibbonBar::IsToolTipEnabled  
 Indica si información sobre herramientas está habilitado o deshabilitado para la barra de la cinta de opciones.  
  
```  
BOOL IsToolTipEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se habilitan las informaciones sobre herramientas; `FALSE` si se deshabilita la información sobre herramientas.  
  
##  <a name="a-nameistransparentcaptiona--cmfcribbonbaristransparentcaption"></a><a name="istransparentcaption"></a>CMFCRibbonBar::IsTransparentCaption  
 Indica si la pantalla está establecida para la combinación de colores de Aero de Windows.  
  
```  
BOOL IsTransparentCaption() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la combinación de colores es Aero de Windows; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonclickbuttona--cmfcribbonbaronclickbutton"></a><a name="onclickbutton"></a>CMFCRibbonBar::OnClickButton  
 Este método se conserva por compatibilidad con versiones anteriores con aplicaciones existentes y no se recomienda para nuevo desarrollo.  
  
```  
virtual void OnClickButton(
    CMFCRibbonButton* pButton,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero al botón que se hizo clic.  
  
 [in] `point`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoneditcontextmenua--cmfcribbonbaroneditcontextmenu"></a><a name="oneditcontextmenu"></a>CMFCRibbonBar::OnEditContextMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnEditContextMenu(
    CMFCRibbonRichEditCtrl* pEdit,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pEdit`  
 [in] `point`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrtlchangeda--cmfcribbonbaronrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonBar::OnRTLChanged  
 Llamado por el marco de trabajo cuando el diseño cambia de dirección.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsRTL`  
 `TRUE`Si el diseño es de derecha a izquierda; `FALSE` si el diseño es de izquierda a derecha.  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta el diseño de todos los controles en la barra de la cinta de opciones para la nueva dirección de diseño.  
  
##  <a name="a-nameonsetaccdataa--cmfcribbonbaronsetaccdata"></a><a name="onsetaccdata"></a>CMFCRibbonBar::OnSetAccData  
 Este método es interno del marco y no está destinado a que se lo llame desde el código del usuario.  
  
```  
BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>Parámetros  
 Long`lVal`  
 El índice del objeto al que se puede acceder.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, FALSE o S_FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonshowribboncontextmenua--cmfcribbonbaronshowribboncontextmenu"></a><a name="onshowribboncontextmenu"></a>CMFCRibbonBar::OnShowRibbonContextMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowRibbonContextMenu(
    CWnd* pWnd,  
    int x,  
    int y,  
    CMFCRibbonBaseElement* pHit);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `x`  
 [in] `y`  
 [in] `pHit`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonshowribbonqatmenua--cmfcribbonbaronshowribbonqatmenu"></a><a name="onshowribbonqatmenu"></a>CMFCRibbonBar::OnShowRibbonQATMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowRibbonQATMenu(
    CWnd* pWnd,  
    int x,  
    int y,  
    CMFCRibbonBaseElement* pHit);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `x`  
 [in] `y`  
 [in] `pHit`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsyskeydowna--cmfcribbonbaronsyskeydown"></a><a name="onsyskeydown"></a>CMFCRibbonBar::OnSysKeyDown  
 Lo llama el marco de trabajo cuando el usuario presiona la tecla F10 o mantiene presionada la tecla ALT y, a continuación, presiona otra tecla.  
  
```  
BOOL OnSysKeyDown(
    CFrameWnd* pFrameWnd,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrameWnd`  
 Puntero a la ventana de marco principal primario de la barra de la cinta de opciones.  
  
 [in] `wParam`  
 Código de tecla virtual de presionar la tecla.  
  
 [in] `lParam`  
 Cuando se presiona la tecla del teclado indicadores de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha procesado el evento de pulsación de tecla; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsyskeyupa--cmfcribbonbaronsyskeyup"></a><a name="onsyskeyup"></a>CMFCRibbonBar::OnSysKeyUp  
 Lo llama el marco de trabajo cuando el usuario suelta una tecla que se presionó cuando se presiona la tecla ALT, la tecla ALT o la tecla F10.  
  
```  
BOOL OnSysKeyUp(
    CFrameWnd* pFrameWnd,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrameWnd`  
 Puntero a la ventana de marco principal primario de la barra de la cinta de opciones.  
  
 [in] `wParam`  
 Código de tecla virtual de la clave que se libera.  
  
 [in] `lParam`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha procesado el evento de pulsación de tecla; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepoptooltipa--cmfcribbonbarpoptooltip"></a><a name="poptooltip"></a>CMFCRibbonBar::PopTooltip  
 Quita una información sobre herramientas de la vista.  
  
```  
void PopTooltip();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepretranslatemessagea--cmfcribbonbarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCRibbonBar::PreTranslateMessage  
 Determina si se procesa el mensaje especificado por la barra de la cinta de opciones.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
 Puntero a un mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha procesado el mensaje de la barra de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerecalclayouta--cmfcribbonbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonBar::RecalcLayout  
 Ajusta el diseño de todos los controles en la barra de la cinta de opciones.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Después del ajuste de diseño, se actualiza la presentación de la barra de cinta.  
  
##  <a name="a-nameremoveallcategoriesa--cmfcribbonbarremoveallcategories"></a><a name="removeallcategories"></a>CMFCRibbonBar::RemoveAllCategories  
 Elimina todas las categorías de la cinta de opciones de la barra de cinta.  
  
```  
void RemoveAllCategories();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método elimina todas las categorías de la cinta de opciones de memoria y de la lista de categorías.  
  
##  <a name="a-nameremoveallfromtabsa--cmfcribbonbarremoveallfromtabs"></a><a name="removeallfromtabs"></a>CMFCRibbonBar::RemoveAllFromTabs  
 Quita todos los elementos de la cinta de opciones del área de pestañas.  
  
```  
void RemoveAllFromTabs();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función si desea quitar todos los elementos que se agregan al área de ficha mediante [CMFCRibbonBar::AddToTabs](#addtotabs) método.  
  
##  <a name="a-nameremovecategorya--cmfcribbonbarremovecategory"></a><a name="removecategory"></a>CMFCRibbonBar::RemoveCategory  
 Elimina la categoría especificada de la cinta de opciones de la barra de cinta.  
  
```  
BOOL RemoveCategory(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero de una categoría en la lista de categorías de la cinta de opciones que se encuentra en la barra de cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha eliminado la categoría especificada de la cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La categoría especificada de la cinta de opciones se elimina de la memoria y de la lista de categorías.  
  
##  <a name="a-namesetactivecategorya--cmfcribbonbarsetactivecategory"></a><a name="setactivecategory"></a>CMFCRibbonBar::SetActiveCategory  
 Establece la categoría de la cinta especificada como la categoría activa.  
  
```  
BOOL SetActiveCategory(
    CMFCRibbonCategory* pCategory,  
    BOOL bForceRestore= FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCategory`  
 Una categoría de cinta que se encuentra en la barra de cinta.  
  
 [in] `bForceRestore`  
 `TRUE`para maximizar la barra de cinta si está minimizado; `FALSE` para mostrar la categoría activa en una ventana emergente si se minimiza la barra de cinta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la categoría especificada se ha establecido como la categoría activa; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La categoría principal de la cinta de opciones no puede estar en la categoría activa.  
  
 Si la categoría especificada por `pCategory` no es aparece, no puede establecerse como la categoría activa.  
  
##  <a name="a-namesetactivemdichilda--cmfcribbonbarsetactivemdichild"></a><a name="setactivemdichild"></a>CMFCRibbonBar::SetActiveMDIChild  
 Asocia los botones de sistema en la barra de cinta que pertenecen a una ventana secundaria de la interfaz de múltiples documentos (MDI) a la ventana secundaria MDI especificada.  
  
```  
void SetActiveMDIChild(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a una ventana secundaria MDI.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetapplicationbuttona--cmfcribbonbarsetapplicationbutton"></a><a name="setapplicationbutton"></a>CMFCRibbonBar::SetApplicationButton  
 Asigna un botón de la cinta de opciones de aplicación a la barra de cinta.  
  
```  
void SetApplicationButton(
    CMFCRibbonApplicationButton* pButton,  
    CSize sizeButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero para el botón de la cinta de opciones de aplicación.  
  
 [in] `sizeButton`  
 El tamaño del botón de la cinta de opciones de aplicación.  
  
### <a name="remarks"></a>Comentarios  
 El botón de la cinta de opciones de aplicación es un botón redondeado grande situado en la esquina superior izquierda del control de la cinta de opciones.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetApplicationButton` método en la `CMFCRibbonBar` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp&3;](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_4.cpp)]  
  
##  <a name="a-namesetelementkeysa--cmfcribbonbarsetelementkeys"></a><a name="setelementkeys"></a>CMFCRibbonBar::SetElementKeys  
 Establece las sugerencias de teclas para todos los elementos de la cinta de opciones que tienen el identificador de comando especificado.  
  
```  
BOOL SetElementKeys(
    UINT uiCmdID,  
    LPCTSTR lpszKeys,  
    LPCTSTR lpszMenuKeys= NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 El identificador de comando de un elemento de la cinta de opciones.  
  
 [in] `lpszKeys`  
 La sugerencia de tecla.  
  
 [in] `lpszMenuKeys`  
 La sugerencia de tecla de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establecen las sugerencias de teclas del elemento de al menos una cinta de opciones; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La sugerencia de tecla de menú opcional es para los elementos de la cinta de opciones con un botón de división que se abre un menú emergente.  
  
##  <a name="a-namesetkeyboardnavigationlevela--cmfcribbonbarsetkeyboardnavigationlevel"></a><a name="setkeyboardnavigationlevel"></a>CMFCRibbonBar::SetKeyboardNavigationLevel  
 Establece el nivel de exploración del teclado como el usuario presiona las sugerencias de teclas que se encuentran en la barra de cinta.  
  
```  
void SetKeyboardNavigationLevel(
    CObject* pLevel,  
    BOOL bSetFocus = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pLevel`  
 Puntero al objeto de navegación de teclado actual.  
  
 [in] `bSetFocus`  
 `TRUE`Para establecer el foco del teclado en la barra de cinta.  
  
### <a name="remarks"></a>Comentarios  
 Navegación mediante el teclado de la barra de cinta se inicia cuando el usuario presiona la tecla ALT o F10. El usuario selecciona el siguiente nivel de navegación presionando keytip en la barra de la cinta de opciones. El usuario puede volver a nivel de exploración anterior presionando la tecla ESC.  
  
##  <a name="a-namesetmaximizemodea--cmfcribbonbarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCRibbonBar::SetMaximizeMode  
 Ajusta la cinta de opciones de la barra cuando el tamaño de la ventana de una ventana secundaria de la interfaz de múltiples documentos (MDI) entra o sale del estado maximizado.  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMax`  
 `TRUE`para mostrar los botones de sistema de una ventana secundaria MDI en la barra de la cinta de opciones. `FALSE` para quitar los botones de sistema de una ventana secundaria MDI de la barra de cinta.  
  
 [in] `pWnd`  
 Puntero a la ventana de marco principal de la barra de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 La barra de la cinta de opciones muestra botones de sistema de una ventana secundaria MDI en la fila de pestañas cuando se maximiza una ventana secundaria MDI.  
  
##  <a name="a-namesetquickaccesscommandsa--cmfcribbonbarsetquickaccesscommands"></a><a name="setquickaccesscommands"></a>CMFCRibbonBar::SetQuickAccessCommands  
 Agrega uno o más elementos de la cinta de opciones a la barra de herramientas de acceso rápido.  
  
```  
void SetQuickAccessCommands(
    const CList<UINT,UINT>& lstCommands,  
    BOOL bRecalcLayout=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lstCommands`  
 La lista de comandos que se coloca en la barra de herramientas de acceso rápido.  
  
 [in] `bRecalcLayout`  
 `TRUE`Si desea volver a dibujar la cinta después de agregar los elementos de la cinta de opciones; `FALSE` en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetQuickAccessCommands` método en la `CMFCRibbonBar` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&8;](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_5.cpp)]  
  
##  <a name="a-namesetquickaccessdefaultstatea--cmfcribbonbarsetquickaccessdefaultstate"></a><a name="setquickaccessdefaultstate"></a>CMFCRibbonBar::SetQuickAccessDefaultState  
 Establece la barra de herramientas de acceso rápido al estado predeterminado.  
  
```  
void SetQuickAccessDefaultState(const CMFCRibbonQuickAccessToolBarDefaultState& state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `state`  
 El estado predeterminado de barra de herramientas de acceso rápido.  
  
### <a name="remarks"></a>Comentarios  
 El estado de la barra de herramientas de acceso rápido incluye una lista de comandos y su visibilidad.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetQuickAccessDefaultState` método en la `CMFCRibbonBar` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#9;](../../mfc/reference/codesnippet/cpp/cmfcribbonbar-class_6.cpp)]  
  
##  <a name="a-namesetquickaccesstoolbarontopa--cmfcribbonbarsetquickaccesstoolbarontop"></a><a name="setquickaccesstoolbarontop"></a>CMFCRibbonBar::SetQuickAccessToolbarOnTop  
 Coloca la barra de herramientas de acceso rápido por encima o debajo de la barra de la cinta de opciones.  
  
```  
void SetQuickAccessToolbarOnTop(BOOL bOnTop);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bOnTop`  
 `TRUE`para colocar la barra de herramientas de acceso rápido encima de la barra de la cinta de opciones; `FALSE` para colocar la barra de herramientas de acceso rápido debajo de la barra de la cinta de opciones.  
  
##  <a name="a-namesettooltipfixedwidtha--cmfcribbonbarsettooltipfixedwidth"></a><a name="settooltipfixedwidth"></a>CMFCRibbonBar::SetTooltipFixedWidth  
 Establece los tamaños grandes y regulares de información sobre herramientas que se fija el ancho de la barra de la cinta de opciones.  
  
```  
void SetTooltipFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nWidthRegular`  
 El ancho, en píxeles, de la información de tamaño fijo normal.  
  
 [in] `nWidthLargeImage`  
 El ancho, en píxeles, de gran tamaño fijo de tamaño información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Si un parámetro en 0 hace que el ancho correspondiente variar.  
  
##  <a name="a-nameshowcategorya--cmfcribbonbarshowcategory"></a><a name="showcategory"></a>CMFCRibbonBar::ShowCategory  
 Muestra u oculta la categoría de la cinta de opciones especificada.  
  
```  
void ShowCategory(
    int nIndex,  
    BOOL bShow=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice de la categoría de cinta de opciones.  
  
 [in] `bShow`  
 Si `TRUE`, mostrar la categoría de cinta de opciones; en caso contrario, ocultar la categoría de cinta de opciones.  
  
##  <a name="a-nameshowcontextcategoriesa--cmfcribbonbarshowcontextcategories"></a><a name="showcontextcategories"></a>CMFCRibbonBar::ShowContextCategories  
 Muestra u oculta las categorías de contexto que tienen el identificador especificado.  
  
```  
void ShowContextCategories(
    UINT uiContextID,  
    BOOL bShow=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiContextID`  
 El identificador de categoría de contexto.  
  
 [in] `bShow`  
 Si `TRUE`, mostrar las categorías que tienen el identificador especificado; en caso contrario, ocultar las categorías que tienen el identificador especificado.  
  
##  <a name="a-nameshowkeytipsa--cmfcribbonbarshowkeytips"></a><a name="showkeytips"></a>CMFCRibbonBar::ShowKeyTips  
 Muestra las sugerencias de teclas para cada elemento de la cinta de opciones en la barra de la cinta de opciones.  
  
```  
void ShowKeyTips();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nametogglemimimizestatea--cmfcribbonbartogglemimimizestate"></a><a name="togglemimimizestate"></a>CMFCRibbonBar::ToggleMimimizeState  
 Alterna la barra de cinta entre los estados minimizado y maximizado.  
  
```  
void ToggleMimimizeState();
```  
  
### <a name="remarks"></a>Comentarios  
 El error ortográfico en el nombre del método es un problema conocido.  
  
 En el estado minimizado, el control de cinta está oculto y solo se muestran las pestañas. Cuando el usuario hace clic en una pestaña, el control de cinta se muestra como una ventana emergente. La ventana se cierra cuando el usuario hace clic fuera o ejecuta un comando.  
  
##  <a name="a-nametranslatechara--cmfcribbonbartranslatechar"></a><a name="translatechar"></a>CMFCRibbonBar::TranslateChar  
 Determina si se procesa el código de carácter de pulsación de tecla especificada por la barra de la cinta de opciones.  
  
```  
virtual BOOL TranslateChar(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nChar`  
 Un código de carácter de pulsación de tecla de usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el código de carácter se ha procesado por la barra de la cinta de opciones. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La característica de sugerencias de teclas permite a los usuarios navegar por la barra de la cinta de opciones mediante el teclado.  
  
##  <a name="a-namegetfocuseda--cmfcribbonbargetfocused"></a><a name="getfocused"></a>CMFCRibbonBar::GetFocused  
 Devuelve un elemento que tiene el foco.  
  
```  
virtual CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento enfocado o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiswindows7looka--cmfcribbonbariswindows7look"></a><a name="iswindows7look"></a>CMFCRibbonBar::IsWindows7Look  
 Indica si la cinta tiene Windows 7 buscar (botón pequeña aplicación rectangular).  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la cinta tiene Windows 7 de búsqueda; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameloadfromresourcea--cmfcribbonbarloadfromresource"></a><a name="loadfromresource"></a>CMFCRibbonBar::LoadFromResource  
 Sobrecargado. Carga una barra de cinta a partir de los recursos de la aplicación.  
  
```  
virtual BOOL LoadFromResource(
    UINT uiXMLResID,  
    LPCTSTR lpszResType = RT_RIBBON,  
    HINSTANCE hInstance = NULL);

 
virtual BOOL LoadFromResource(
    LPCTSTR lpszXMLResID,  
    LPCTSTR lpszResType = RT_RIBBON,  
    HINSTANCE hInstance = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `uiXMLResID`  
 Especifica el recurso de cadena del identificador de XML con información de la barra de la cinta de opciones.  
  
 `lpszResType`  
 Especifica el tipo de recurso ubicado en `uiXMLResID`.  
  
 `hInstance`  
 Identificador del módulo cuyo archivo ejecutable contiene el recurso. Si `hInstance` es `NULL`, el sistema carga el recurso desde el módulo que se usó para crear el proceso actual.  
  
 `lpszXMLResID`  
 Especifica el identificador de recurso (en forma de cadena) con información de la barra de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la carga se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesavetoxmlbuffera--cmfcribbonbarsavetoxmlbuffer"></a><a name="savetoxmlbuffer"></a>CMFCRibbonBar::SaveToXMLBuffer  
 Guarda la barra de cinta en un búfer.  
  
```  
UINT SaveToXMLBuffer(LPBYTE* ppBuffer) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppBuffer`  
 Esta función devuelve `ppBuffer` apunta a un búfer asignado por este método y contiene información de la barra de la cinta de opciones en formato XML.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesavetoxmlfilea--cmfcribbonbarsavetoxmlfile"></a><a name="savetoxmlfile"></a>CMFCRibbonBar::SaveToXMLFile  
 La barra de cinta se guarda en un archivo XML.  
  
```  
BOOL SaveToXMLFile(LPCTSTR lpszFilePath) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFilePath`  
 Especifica el archivo de salida.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetwindows7looka--cmfcribbonbarsetwindows7look"></a><a name="setwindows7look"></a>CMFCRibbonBar::SetWindows7Look  
 Habilita o deshabilita la apariencia de Windows 7 (botón aplicación rectangular pequeño) de la cinta de opciones.  
  
```  
void SetWindows7Look(
    BOOL bWindows7Look,  
    BOOL bRecalc = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bWindows7Look`  
 `TRUE`establece la apariencia de Windows 7; `FALSE` en caso contrario.  
  
 `bRecalc`  
 `TRUE`vuelve a calcular el diseño de la cinta de opciones; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPane](../../mfc/reference/cpane-class.md)   
 [Clase de CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)   
 [Clase CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)   
 [Clase CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [Tutorial: Actualizar la aplicación Scribble MFC](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)




