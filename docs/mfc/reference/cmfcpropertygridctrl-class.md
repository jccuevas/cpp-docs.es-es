---
title: Clase CMFCPropertyGridCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridCtrl::get_accValue method
- CMFCPropertyGridCtrl::accHitTest method
- CMFCPropertyGridCtrl::get_accState method
- CMFCPropertyGridCtrl::accLocation method
- CMFCPropertyGridCtrl::get_accChild method
- CMFCPropertyGridCtrl::get_accName method
- CMFCPropertyGridCtrl::PreTranslateMessage method
- CMFCPropertyGridCtrl::get_accRole method
- CMFCPropertyGridCtrl::get_accDefaultAction method
- CMFCPropertyGridCtrl class
- CMFCPropertyGridCtrl::get_accDescription method
ms.assetid: 95877cae-2311-4a2a-9031-0c8c3cf0a5f9
caps.latest.revision: 35
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
ms.openlocfilehash: 93611d1b52d6372a81b91f08c5a5c7b215b584e3
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridctrl-class"></a>Clase CMFCPropertyGridCtrl
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Admite un control de cuadrícula de propiedades editables que puede mostrar propiedades en orden alfabético o jerárquico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)|Construye un objeto `CMFCPropertyGridCtrl`.|  
|`CMFCPropertyGridCtrl::~CMFCPropertyGridCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCPropertyGridCtrl::accHitTest`|El marco llama a este método para recuperar el elemento u objeto secundario situado en un punto dado de la pantalla. (Invalida [CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest).)|  
|`CMFCPropertyGridCtrl::accLocation`|El marco llama a este método para recuperar la ubicación actual del objeto especificado en la pantalla. (Invalida [CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation).)|  
|[CMFCPropertyGridCtrl::accSelect](#accselect)|El marco llama a este método para modificar la selección o desplazar el foco de teclado del objeto especificado. (Invalida [CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect).)|  
|[CMFCPropertyGridCtrl::AddProperty](#addproperty)|Agrega una nueva propiedad a un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::AlwaysShowUserToolTip](#alwaysshowusertooltip)||  
|[CMFCPropertyGridCtrl::CloseColorPopup](#closecolorpopup)|Cierra el cuadro de diálogo de selección de color.|  
|[CMFCPropertyGridCtrl::Create](#create)|Crea un control de cuadrícula de propiedad y lo adjunta al objeto de control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::DeleteProperty](#deleteproperty)|Elimina la propiedad especificada desde el control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::DrawControlBarColors](#drawcontrolbarcolors)||  
|[CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea)|Habilita o deshabilita el área de descripción que se muestra debajo de la lista de propiedades.|  
|[CMFCPropertyGridCtrl::EnableHeaderCtrl](#enableheaderctrl)|Habilita o deshabilita el control de encabezado en la parte superior del control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::EnsureVisible](#ensurevisible)|Se desplaza a un control de cuadrícula de propiedades y expande los elementos de propiedad hasta que la propiedad especificada está visible.|  
|[CMFCPropertyGridCtrl::ExpandAll](#expandall)|Expande o contrae todos los nodos de control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::FindItemByData](#finditembydata)|Recupera la propiedad asociada definida por el usuario `DWORD` valor.|  
|`CMFCPropertyGridCtrl::get_accChild`|El marco llama a este método para recuperar la dirección de una interfaz `IDispatch` del elemento secundario especificado. (Invalida [CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild).)|  
|[CMFCPropertyGridCtrl::get_accChildCount](#get_accchildcount)|El marco llama a este método para recuperar el número de elementos secundarios que pertenecen a este objeto. (Invalida [CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount).)|  
|`CMFCPropertyGridCtrl::get_accDefaultAction`|El marco llama a este método para recuperar una cadena que describe la acción predeterminada del objeto. (Invalida [CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction).)|  
|`CMFCPropertyGridCtrl::get_accDescription`|El marco llama a este método para recuperar una cadena que describe la apariencia visual del objeto especificado. (Invalida [CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription).)|  
|[CMFCPropertyGridCtrl::get_accFocus](#get_accfocus)|El marco llama a este método para recuperar el objeto que tiene el foco de teclado. (Invalida [CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus).)|  
|[CMFCPropertyGridCtrl::get_accHelp](#get_acchelp)|Llamado por el marco para recuperar un objeto `Help` cadena de propiedad. (Invalida [CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp).)|  
|[CMFCPropertyGridCtrl::get_accHelpTopic](#get_acchelptopic)|Llamado por el marco para recuperar la ruta de acceso completa de la `WinHelp`archivo asociado con el objeto especificado y el identificador del tema correspondiente dentro de ese archivo. (Invalida [CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic).)|  
|[CMFCPropertyGridCtrl::get_accKeyboardShortcut](#get_acckeyboardshortcut)|El marco llama a este método para recuperar la tecla de método abreviado o la tecla de acceso del objeto especificado. (Invalida [CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut).)|  
|`CMFCPropertyGridCtrl::get_accName`|El marco llama a este método para recuperar el nombre del objeto especificado. (Invalida [CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname).)|  
|`CMFCPropertyGridCtrl::get_accRole`|El marco llama a este método para recuperar información que describe el rol del objeto especificado. (Invalida [CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole).)|  
|[CMFCPropertyGridCtrl::get_accSelection](#get_accselection)|El marco llama a este método para recuperar el elemento secundario seleccionado de este objeto. (Invalida [CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection).)|  
|`CMFCPropertyGridCtrl::get_accState`|El marco llama a este método para recuperar el estado actual del objeto especificado. (Invalida [CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate).)|  
|`CMFCPropertyGridCtrl::get_accValue`|El marco llama a este método para recuperar el valor del objeto especificado. (Invalida [CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue).)|  
|[CMFCPropertyGridCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo del control de cuadrícula de propiedad actual.|  
|[CMFCPropertyGridCtrl::GetBoldFont](#getboldfont)|Recupera la fuente de Windows que del texto en la cuadrícula de propiedades actual del control de estilo de negrita.|  
|[CMFCPropertyGridCtrl::GetCurSel](#getcursel)|Recupera la propiedad seleccionada actualmente.|  
|[CMFCPropertyGridCtrl::GetCustomColors](#getcustomcolors)|Recupera los colores personalizados que están definidos actualmente para los elementos de control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::GetDescriptionHeight](#getdescriptionheight)|Recupera el alto del área de descripción situado en la parte inferior del control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::GetDescriptionRows](#getdescriptionrows)|Recupera el número de filas en el área de descripción del control de cuadrícula de propiedad actual.|  
|[CMFCPropertyGridCtrl::GetHeaderCtrl](#getheaderctrl)|Recupera el interno [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que utiliza el marco de trabajo para mostrar el control de cuadrícula de propiedad actuales del objeto.|  
|[CMFCPropertyGridCtrl::GetHeaderHeight](#getheaderheight)|Recupera el alto del encabezado de control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::GetLeftColumnWidth](#getleftcolumnwidth)|Recupera el ancho de la columna izquierda del control de cuadrícula propiedad actual, que contiene el nombre de cada propiedad.|  
|[CMFCPropertyGridCtrl::GetListRect](#getlistrect)|Recupera el rectángulo delimitador del control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::GetProperty](#getproperty)|Recupera un puntero al objeto de propiedad que se corresponde con el índice especificado de un elemento de control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetPropertyColumnWidth](#getpropertycolumnwidth)|Recupera el ancho actual de la columna que contiene los valores de propiedad.|  
|[CMFCPropertyGridCtrl::GetPropertyCount](#getpropertycount)|Recupera el número de propiedades de un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetRowHeight](#getrowheight)|Recupera el alto de una fila en el control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetScrollBarCtrl](#getscrollbarctrl)|Recupera un puntero a la barra de desplazamiento en el control de cuadrícula de propiedad. (Invalida [CWnd::GetScrollBarCtrl](../../mfc/reference/cwnd-class.md#getscrollbarctrl).)|  
|[CMFCPropertyGridCtrl::GetTextColor](#gettextcolor)|Recupera el color del texto de los elementos de propiedad en el control de cuadrícula de propiedad actual.|  
|`CMFCPropertyGridCtrl::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCPropertyGridCtrl::HitTest](#hittest)|Recupera un puntero al objeto de propiedad que corresponde a un elemento de control de cuadrícula de propiedades, si es un punto especificado en el elemento. Este método también indica el área en el control de cuadrícula de propiedad que contiene el punto.|  
|[CMFCPropertyGridCtrl::InitHeader](#initheader)|Inicializa el interno [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que utiliza el marco de trabajo para mostrar el control de cuadrícula de propiedad actuales del objeto.|  
|[CMFCPropertyGridCtrl::IsAlphabeticMode](#isalphabeticmode)|Indica si un control de cuadrícula de propiedades está en modo alfabético.|  
|[CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip](#isalwaysshowusertooltip)||  
|[CMFCPropertyGridCtrl::IsDescriptionArea](#isdescriptionarea)|Indica si se muestra el área de descripción del control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::IsGroupNameFullWidth](#isgroupnamefullwidth)|Indica si cada nombre de grupo se muestra en el ancho del control de cuadrícula de propiedad actual.|  
|[CMFCPropertyGridCtrl::IsHeaderCtrl](#isheaderctrl)|Indica si se muestra el control de encabezado.|  
|[CMFCPropertyGridCtrl::IsMarkModifiedProperties](#ismarkmodifiedproperties)|Indica cómo el control de cuadrícula de propiedades muestra las propiedades modificadas.|  
|[CMFCPropertyGridCtrl::IsShowDragContext](#isshowdragcontext)|Indica si el marco de trabajo se vuelve a dibujar las columnas de nombre y valor del control de cuadrícula de propiedad actual cuando un usuario cambia el tamaño de las columnas.|  
|[CMFCPropertyGridCtrl::IsVSDotNetLook](#isvsdotnetlook)|Indica si la apariencia del control de cuadrícula de propiedad es en el estilo que usa .NET de VS.|  
|[CMFCPropertyGridCtrl::MarkModifiedProperties](#markmodifiedproperties)|Especifica cómo mostrar las propiedades modificadas.|  
|`CMFCPropertyGridCtrl::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCPropertyGridCtrl::RemoveAll](#removeall)|Quita todos los objetos de propiedad de un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::ResetOriginalValues](#resetoriginalvalues)|Restablece el valor original de todas las propiedades.|  
|[CMFCPropertyGridCtrl::SetAlphabeticMode](#setalphabeticmode)|Establece o restablece el modo alfabético.|  
|[CMFCPropertyGridCtrl::SetBoolLabels](#setboollabels)|Especifica el texto de las etiquetas de tipo Boolean.|  
|[CMFCPropertyGridCtrl::SetCurSel](#setcursel)|Selecciona una propiedad de un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::SetCustomColors](#setcustomcolors)|Especifica los colores personalizados para distintos elementos de control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::SetDescriptionRows](#setdescriptionrows)|Especifica el número de filas que se muestran en la sección de descripción del control de cuadrícula de propiedad actual.|  
|[CMFCPropertyGridCtrl::SetGroupNameFullWidth](#setgroupnamefullwidth)|Especifica si se muestra el ancho completo del nombre de categoría de un grupo de propiedades en el control de cuadrícula de propiedad actual.|  
|[CMFCPropertyGridCtrl::SetListDelimiter](#setlistdelimiter)|Define un carácter que se utilizará como delimitador en una lista de valores de propiedad.|  
|[CMFCPropertyGridCtrl::SetShowDragContext](#setshowdragcontext)|Especifica si el marco de trabajo se vuelve a dibujar las columnas de nombre y valor del control de cuadrícula de propiedad actual cuando un usuario cambia el tamaño de las columnas.|  
|[CMFCPropertyGridCtrl::SetVSDotNetLook](#setvsdotnetlook)|Establece la apariencia del control de cuadrícula de propiedad en el estilo que se utiliza en VS.NET.|  
|[CMFCPropertyGridCtrl::UpdateColor](#updatecolor)|Establece el valor de color de la propiedad de color seleccionado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::AdjustLayout](#adjustlayout)|Vuelve a dibujar el control de cuadrícula de propiedades y sus propiedades.|  
|[CMFCPropertyGridCtrl::CompareProps](#compareprops)|Llamado por el control de cuadrícula de propiedad para ordenar las propiedades.|  
|[CMFCPropertyGridCtrl::EditItem](#edititem)|Lo llama el marco de trabajo cuando el usuario comienza a modificar una propiedad.|  
|[CMFCPropertyGridCtrl::EndEditItem](#endedititem)|Lo llama el marco de trabajo cuando el usuario deja de modificar una propiedad.|  
|[CMFCPropertyGridCtrl::Init](#init)|Llamado por el marco para inicializar un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::OnChangeSelection](#onchangeselection)|Llamado por el marco de trabajo cuando se cambia la selección actual.|  
|[CMFCPropertyGridCtrl::OnClickButton](#onclickbutton)|Lo llama el marco de trabajo cuando se hace clic en un botón de la propiedad.|  
|[CMFCPropertyGridCtrl::OnDrawBorder](#ondrawborder)|Llamado por el marco para dibujar un borde alrededor de un control de cuadrícula de propiedad.|  
|[CMFCPropertyGridCtrl::OnDrawDescription](#ondrawdescription)|Llamado por el marco para dibujar el área de descripción y mostrar el texto de descripción.|  
|[CMFCPropertyGridCtrl::OnDrawList](#ondrawlist)|Llamado por el marco de trabajo para mostrar la lista de propiedades en el control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::OnDrawProperty](#ondrawproperty)|Llamado por el marco de trabajo para mostrar una propiedad.|  
|[CMFCPropertyGridCtrl::OnPropertyChanged](#onpropertychanged)|Llamado por el marco de trabajo cuando se cambia el valor de una propiedad.|  
|[CMFCPropertyGridCtrl::OnSelectCombo](#onselectcombo)|Lo llama el marco de trabajo cuando se selecciona una propiedad que contiene un control de cuadro combinado.|  
|[CMFCPropertyGridCtrl::ValidateItemData](#validateitemdata)|Llamado por el marco para validar los datos de propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMFCPropertyGridCtrl` clase muestra un control de cuadrícula de propiedades que contiene propiedades modificables que se deriva de la [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md) clase. Cada propiedad puede representar un tipo y puede contener subelementos. El control de cuadrícula de propiedad es compatible con un área de tamaño variable en la parte inferior que se puede mostrar la descripción de una propiedad seleccionada.  
  
 Para utilizar un control de cuadrícula de propiedades, construir una `CMFCPropertyGridCtrl` de objetos y, a continuación, llame a la [CMFCPropertyGridCtrl::Create](#create) método. Utilice la [CMFCPropertyGridCtrl::AddProperty](#addproperty) para agregar propiedades a la lista.  
  
## <a name="selection-properties"></a>Propiedades de selección  
 Que representa un valor, en lugar de un elemento de propiedad puede iniciar un cuadro de diálogo que permite al usuario seleccionar un color, el archivo o la fuente.  
  
 La siguiente tabla enumera cuatro tipos de propiedad de selección:  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[Clase CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)|Una propiedad de propósito general que se utiliza para especificar el valor de cadenas, booleanos, fechas y así sucesivamente.|  
|[Clase CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)|Una propiedad que se utiliza para seleccionar un valor de color.|  
|[Clase CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)|Una propiedad que se utiliza para seleccionar un archivo.|  
|[Clase CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)|Una propiedad que se utiliza para seleccionar una fuente.|  
  
## <a name="illustrations"></a>Ilustraciones  
 Las ilustraciones siguientes muestran un control de cuadrícula de propiedades que muestra las propiedades de dos maneras. La primera ilustración muestra las propiedades jerárquicamente y la segunda muestra propiedades alfabéticamente.  
  
 ![Lista de propiedades PropertySheet](../../mfc/reference/media/proplist.png "proplist")  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un objeto de control de cuadrícula de propiedad mediante varios métodos en la `CMFCPropertyGridCtrl` clase. En el ejemplo se muestra cómo habilitar el control de encabezado, habilitar el área de descripción y establecer la apariencia del control de cuadrícula de propiedad. El ejemplo también muestra cómo establecer el modo alfabético para el control mediante el cual se ordena el control de todas las propiedades que contiene su nombre de propiedad y cómo establecer los colores personalizados para distintos elementos del control de cuadrícula de propiedad. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#14;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls Nº&16;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls&#20;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_3.cpp)]  
[!code-cpp[21 NVC_MFC_NewControls](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_4.cpp)]  
[!code-cpp[NVC_MFC_NewControls&#24;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_5.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridctrl.h  
  
##  <a name="a-nameaccselecta--cmfcpropertygridctrlaccselect"></a><a name="accselect"></a>CMFCPropertyGridCtrl::accSelect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT accSelect(
    long flagsSelect,  
    VARIANT varChild);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `flagsSelect`  
 [in] `varChild`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddpropertya--cmfcpropertygridctrladdproperty"></a><a name="addproperty"></a>CMFCPropertyGridCtrl::AddProperty  
 Agrega una nueva propiedad a un control de cuadrícula de propiedades.  
  
```  
int AddProperty(
    CMFCPropertyGridProperty* pProp,  
    BOOL bRedraw=TRUE,  
    BOOL bAdjustLayout=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a una propiedad.  
  
 [in] `bRedraw`  
 `TRUE`Para volver a dibujar la propiedad inmediatamente; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
 [in] `bAdjustLayout`  
 `TRUE`Para volver a calcular cómo dibujar el texto y el valor de la propiedad y, a continuación, dibuje la propiedad; `FALSE` utilizar cálculos existentes para dibujar la propiedad. El valor predeterminado es `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si este método se realiza correctamente, el índice de base cero de la posición en el control de cuadrícula de propiedades donde se agrega la propiedad; en caso contrario, es -1.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega un puntero a la propiedad especificada al final de la lista de propiedades en el control de cuadrícula de propiedad. No destruir las propiedades o permitirles que salen del ámbito antes de destruir el control de cuadrícula. Cuando haya terminado con el control de cuadrícula de propiedades, llame a [CMFCPropertyGridCtrl::RemoveAll](#removeall) para eliminar todas las propiedades agregadas. El método AddProperty produce un error si la propiedad especificada ya se ha agregado a la lista.  
  
##  <a name="a-nameadjustlayouta--cmfcpropertygridctrladjustlayout"></a><a name="adjustlayout"></a>CMFCPropertyGridCtrl::AdjustLayout  
 Vuelve a dibujar el control de cuadrícula de propiedades y sus propiedades.  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método vuelve a calcular cómo dibujar el control de cuadrícula de propiedad completa y sus propiedades, incluidas imágenes, fuentes y controles.  
  
##  <a name="a-namealwaysshowusertooltipa--cmfcpropertygridctrlalwaysshowusertooltip"></a><a name="alwaysshowusertooltip"></a>CMFCPropertyGridCtrl::AlwaysShowUserToolTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AlwaysShowUserToolTip(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameclosecolorpopupa--cmfcpropertygridctrlclosecolorpopup"></a><a name="closecolorpopup"></a>CMFCPropertyGridCtrl::CloseColorPopup  
 Cierra el cuadro de diálogo de selección de color.  
  
```  
virtual void CloseColorPopup();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el cuadro de diálogo de selección de color, consulte [CMFCPropertyGridColorProperty clase](../../mfc/reference/cmfcpropertygridcolorproperty-class.md).  
  
##  <a name="a-namecmfcpropertygridctrla--cmfcpropertygridctrlcmfcpropertygridctrl"></a><a name="cmfcpropertygridctrl"></a>CMFCPropertyGridCtrl::CMFCPropertyGridCtrl  
 Construye un objeto `CMFCPropertyGridCtrl`.  
  
```  
CMFCPropertyGridCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecomparepropsa--cmfcpropertygridctrlcompareprops"></a><a name="compareprops"></a>CMFCPropertyGridCtrl::CompareProps  
 Llamado por el control de cuadrícula de propiedad para ordenar las propiedades.  
  
```  
virtual int CompareProps(
    const CMFCPropertyGridProperty* pProp1,  
    const CMFCPropertyGridProperty* pProp2) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pProp1`  
 Un puntero a una propiedad.  
  
 `pProp2`  
 Un puntero a una propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
  
|Valor devuelto|Descripción|  
|------------------|-----------------|  
|< 0|El nombre de la `pProp1` parámetro es menor que el nombre de la `pProp2` parámetro.|  
|0|El nombre de la `pProp1` parámetro es igual al nombre de la `pProp2` parámetro.|  
|> 0|El nombre de la `pProp1` objeto es mayor que el nombre de la `pProp2` parámetro.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método utiliza el [CString::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método para comparar los `CMFCPropertyGridProperty::m_strName` miembros de los parámetros especificados.  
  
##  <a name="a-namecreatea--cmfcpropertygridctrlcreate"></a><a name="create"></a>CMFCPropertyGridCtrl::Create  
 Crea un control de cuadrícula de propiedad y lo adjunta al objeto de control de cuadrícula de propiedad.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyle`  
 Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Coordenadas de un rectángulo delimitador que especifica el tamaño y la posición de la ventana de cliente de `pParentWnd`.  
  
 [in] `pParentWnd`  
 Puntero a la ventana primaria. No debe ser `NULL`.  
  
 [in] `nID`  
 El identificador de la ventana secundaria.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para crear un control de cuadrícula de propiedades, la primera llamada [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl) para construir un objeto de cuadrícula de propiedad. A continuación, llamar a `CMFCPropertyGridCtrl::Create`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método `CMFCPropertyGridCtrl` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#15;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_6.cpp)]  
  
##  <a name="a-namedeletepropertya--cmfcpropertygridctrldeleteproperty"></a><a name="deleteproperty"></a>CMFCPropertyGridCtrl::DeleteProperty  
 Elimina la propiedad especificada desde el control de cuadrícula de propiedades.  
  
```  
BOOL DeleteProperty(
    CMFCPropertyGridProperty*& pProp,  
    BOOL bRedraw=TRUE,  
    BOOL bAdjustLayout=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a una propiedad.  
  
 [in] `bRedraw`  
 `TRUE`Para volver a dibujar el control de cuadrícula de propiedad; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
 [in] `bAdjustLayout`  
 `TRUE`Para volver a calcular cómo dibujar todo el texto, imágenes y elementos en el control de cuadrícula de propiedad y, a continuación, dibuje el control; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para eliminar una propiedad y los elementos secundarios, desde el control de cuadrícula de propiedades.  
  
##  <a name="a-namedrawcontrolbarcolorsa--cmfcpropertygridctrldrawcontrolbarcolors"></a><a name="drawcontrolbarcolors"></a>CMFCPropertyGridCtrl::DrawControlBarColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL DrawControlBarColors() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameedititema--cmfcpropertygridctrledititem"></a><a name="edititem"></a>CMFCPropertyGridCtrl::EditItem  
 Lo llama el marco de trabajo cuando el usuario comienza a modificar una propiedad.  
  
```  
virtual BOOL EditItem(
    CMFCPropertyGridProperty* pProp,  
    LPPOINT lptClick=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a una propiedad.  
  
 [in] `lptClick`  
 El punto en el control de cuadrícula de propiedad que el usuario hizo clic para comenzar la operación de edición. El punto se encuentra en las coordenadas de cliente del control. El valor predeterminado es `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenabledescriptionareaa--cmfcpropertygridctrlenabledescriptionarea"></a><a name="enabledescriptionarea"></a>CMFCPropertyGridCtrl::EnableDescriptionArea  
 Habilita o deshabilita el área de descripción que se muestra debajo de la lista de propiedades en el control de cuadrícula de propiedad.  
  
```  
void EnableDescriptionArea(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el área de descripción; `FALSE` para deshabilitar el área de descripción. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El área de descripción se muestra en la parte inferior del control de cuadrícula de propiedad. De forma predeterminada, el área de descripción está deshabilitado y no es visible.  
  
##  <a name="a-nameenableheaderctrla--cmfcpropertygridctrlenableheaderctrl"></a><a name="enableheaderctrl"></a>CMFCPropertyGridCtrl::EnableHeaderCtrl  
 Habilita o deshabilita el control de encabezado en la parte superior del control de cuadrícula de propiedad.  
  
```  
void EnableHeaderCtrl(
    BOOL bEnable=TRUE,  
    LPCTSTR lpszLeftColumn=_T("Property"),  
    LPCTSTR lpszRightColumn=_T("Value"));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el control de encabezado; `FALSE` para deshabilitar el control de encabezado. El valor predeterminado es `TRUE`.  
  
 [in] `lpszLeftColumn`  
 El título de la columna izquierda del control de encabezado. El valor predeterminado es **propiedad**.  
  
 [in] `lpszRightColumn`  
 El título de la columna derecha del control de encabezado. El valor predeterminado es **valor**.  
  
##  <a name="a-nameendedititema--cmfcpropertygridctrlendedititem"></a><a name="endedititem"></a>CMFCPropertyGridCtrl::EndEditItem  
 Lo llama el marco de trabajo cuando el usuario termina de modificar una propiedad.  
  
```  
virtual BOOL EndEditItem(BOOL bUpdateData=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUpdateData`  
 `TRUE`para especificar que se deben validar los datos de la propiedad modificada cuando la operación de edición es completa; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la operación de edición finaliza correctamente; `FALSE` si los datos de la propiedad modificada no están válidos o si debe continuar la operación de edición.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameensurevisiblea--cmfcpropertygridctrlensurevisible"></a><a name="ensurevisible"></a>CMFCPropertyGridCtrl::EnsureVisible  
 Se desplaza a un control de cuadrícula de propiedades y expande los elementos de propiedad hasta que la propiedad especificada está visible.  
  
```  
void EnsureVisible(
    CMFCPropertyGridProperty* pProp,  
    BOOL bExpandParents=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a una propiedad.  
  
 [in] `bExpandParents`  
 `TRUE`para expandir los elementos primarios para mostrar la propiedad especificada; de lo contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameexpandalla--cmfcpropertygridctrlexpandall"></a><a name="expandall"></a>CMFCPropertyGridCtrl::ExpandAll  
 Expande o contrae todos los nodos de control de cuadrícula de propiedad.  
  
```  
void ExpandAll(BOOL bExpand=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bExpand`  
 `TRUE`para expandir todos los nodos; `FALSE` para contraer todos los nodos. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefinditembydataa--cmfcpropertygridctrlfinditembydata"></a><a name="finditembydata"></a>CMFCPropertyGridCtrl::FindItemByData  
 Recupera la propiedad asociada definida por el usuario `DWORD` valor.  
  
```  
CMFCPropertyGridProperty* FindItemByData(
    DWORD_PTR dwData,  
    BOOL bSearchSubItems=TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Valor `DWORD`.  
  
 [in] `bSearchSubItems`  
 `TRUE`para buscar los elementos secundarios de la propiedad; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de propiedad asociada si este método se realiza correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl) constructor o [CMFCPropertyGridProperty::SetData](../../mfc/reference/cmfcpropertygridproperty-class.md#setdata) para asociar una `DWORD` con una propiedad.  
  
##  <a name="a-namegetaccchildcounta--cmfcpropertygridctrlgetaccchildcount"></a><a name="get_accchildcount"></a>CMFCPropertyGridCtrl::get_accChildCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accChildCount(long* pcountChildren);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pcountChildren`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetaccfocusa--cmfcpropertygridctrlgetaccfocus"></a><a name="get_accfocus"></a>CMFCPropertyGridCtrl::get_accFocus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accFocus(VARIANT* pvarChild);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pvarChild`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetacchelpa--cmfcpropertygridctrlgetacchelp"></a><a name="get_acchelp"></a>CMFCPropertyGridCtrl::get_accHelp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accHelp(
    VARIANT varChild,  
    BSTR* pszHelp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `varChild`  
 [in] `pszHelp`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetacchelptopica--cmfcpropertygridctrlgetacchelptopic"></a><a name="get_acchelptopic"></a>CMFCPropertyGridCtrl::get_accHelpTopic  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszHelpFile`  
 [in] `varChild`  
 [in] `pidTopic`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetacckeyboardshortcuta--cmfcpropertygridctrlgetacckeyboardshortcut"></a><a name="get_acckeyboardshortcut"></a>CMFCPropertyGridCtrl::get_accKeyboardShortcut  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accKeyboardShortcut(
    VARIANT varChild,  
    BSTR* pszKeyboardShortcut);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `varChild`  
 [in] `pszKeyboardShortcut`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetaccselectiona--cmfcpropertygridctrlgetaccselection"></a><a name="get_accselection"></a>CMFCPropertyGridCtrl::get_accSelection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pvarChildren`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetbkcolora--cmfcpropertygridctrlgetbkcolor"></a><a name="getbkcolor"></a>CMFCPropertyGridCtrl::GetBkColor  
 Recupera el color de fondo del control de cuadrícula de propiedad actual.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el color que el marco de trabajo que se usa para dibujar el fondo del control de cuadrícula de propiedad actual. El [CMFCPropertyGridCtrl::GetTextColor](#gettextcolor) método recupera el color de primer plano.  
  
##  <a name="a-namegetboldfonta--cmfcpropertygridctrlgetboldfont"></a><a name="getboldfont"></a>CMFCPropertyGridCtrl::GetBoldFont  
 Recupera la fuente de Windows que se utiliza para dibujar texto en el control de cuadrícula de propiedad actual en estilo negrita.  
  
```  
CFont& GetBoldFont();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [CFont](../../mfc/reference/cfont-class.md) objeto que describe las características de una fuente en negrita.  
  
##  <a name="a-namegetcursela--cmfcpropertygridctrlgetcursel"></a><a name="getcursel"></a>CMFCPropertyGridCtrl::GetCurSel  
 Recupera la propiedad seleccionada actualmente.  
  
```  
CMFCPropertyGridProperty* GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de propiedad que corresponde al elemento seleccionado en el control de cuadrícula de propiedad.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcustomcolorsa--cmfcpropertygridctrlgetcustomcolors"></a><a name="getcustomcolors"></a>CMFCPropertyGridCtrl::GetCustomColors  
 Recupera los colores personalizados que están definidos actualmente para los elementos de control de cuadrícula de propiedad.  
  
```  
void GetCustomColors(
    COLORREF& clrBackground,  
    COLORREF& clrText,  
    COLORREF& clrGroupBackground,  
    COLORREF& clrGroupText,  
    COLORREF& clrDescriptionBackground,  
    COLORREF& clrDescriptionText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `clrBackground`  
 El color de fondo de los valores de propiedad.  
  
 [out] `clrText`  
 El color de los nombres de propiedad y el texto del valor de propiedad.  
  
 [out] `clrGroupBackground`  
 El color de fondo de un grupo de propiedades.  
  
 [out] `clrGroupText`  
 El color del texto en el grupo de propiedades.  
  
 [out] `clrDescriptionBackground`  
 El color de fondo del área de descripción.  
  
 [out] `clrDescriptionText`  
 El color del texto en el área de descripción.  
  
 [out] `clrLine`  
 El color de las líneas que se dibujan entre las propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::SetCustomColors](#setcustomcolors) método definir colores personalizados.  
  
##  <a name="a-namegetdescriptionheighta--cmfcpropertygridctrlgetdescriptionheight"></a><a name="getdescriptionheight"></a>CMFCPropertyGridCtrl::GetDescriptionHeight  
 Recupera el alto del área de descripción, que se encuentra en la parte inferior del control de cuadrícula de propiedad.  
  
```  
int GetDescriptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del área de descripción, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El alto del área de descripción se calcula automáticamente y se establece en 1/4 el alto del control de cuadrícula de propiedad.  
  
 Utilice la [CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea) método para mostrar u ocultar el área de descripción. Utilice la [CMFCPropertyGridCtrl::IsDescriptionArea](#isdescriptionarea) método para determinar si el área de descripción se mostrará u ocultará.  
  
##  <a name="a-namegetdescriptionrowsa--cmfcpropertygridctrlgetdescriptionrows"></a><a name="getdescriptionrows"></a>CMFCPropertyGridCtrl::GetDescriptionRows  
 Recupera el número de filas en el área de descripción del control de cuadrícula de propiedad actual.  
  
```  
int GetDescriptionRows() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas en el área de descripción del control de cuadrícula de propiedad actual.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl) constructor inicializa el área de descripción en 3 filas.  
  
##  <a name="a-namegetheaderctrla--cmfcpropertygridctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCPropertyGridCtrl::GetHeaderCtrl  
 Recupera el interno [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que utiliza el marco de trabajo para mostrar el control de cuadrícula de propiedad actuales del objeto.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a un objeto `CMFCHeaderCtrl`.  
  
##  <a name="a-namegetheaderheighta--cmfcpropertygridctrlgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertyGridCtrl::GetHeaderHeight  
 Recupera el alto del encabezado de un control de cuadrícula de propiedades.  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del encabezado, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetleftcolumnwidtha--cmfcpropertygridctrlgetleftcolumnwidth"></a><a name="getleftcolumnwidth"></a>CMFCPropertyGridCtrl::GetLeftColumnWidth  
 Recupera el ancho de la columna izquierda del control de cuadrícula propiedad actual, que contiene el nombre de cada propiedad.  
  
```  
int GetLeftColumnWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de la columna nombre.  
  
### <a name="remarks"></a>Comentarios  
 La columna derecha de un control de cuadrícula de propiedad contiene el valor de cada propiedad.  
  
##  <a name="a-namegetlistrecta--cmfcpropertygridctrlgetlistrect"></a><a name="getlistrect"></a>CMFCPropertyGridCtrl::GetListRect  
 Recupera el rectángulo delimitador del control de cuadrícula de propiedad.  
  
```  
CRect GetListRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo delimitador del control de cuadrícula de propiedad. Este rectange no incluye el encabezado y el área de descripción.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpropertya--cmfcpropertygridctrlgetproperty"></a><a name="getproperty"></a>CMFCPropertyGridCtrl::GetProperty  
 Recupera un puntero al objeto de propiedad que corresponde al índice especificado de un elemento en un control de cuadrícula de propiedades.  
  
```  
CMFCPropertyGridProperty* GetProperty(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero de un elemento de control de cuadrícula de propiedades.  
  
 Este método valida si el `nIndex` parámetro es menor que cero o mayor o igual que el número de propiedades.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de propiedad que corresponde al índice especificado, si este método se realiza correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpropertycolumnwidtha--cmfcpropertygridctrlgetpropertycolumnwidth"></a><a name="getpropertycolumnwidth"></a>CMFCPropertyGridCtrl::GetPropertyColumnWidth  
 Recupera el ancho actual de la columna que contiene los valores de propiedad.  
  
```  
int GetPropertyColumnWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho actual de la columna que contiene los valores de propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La columna a la derecha en el control de cuadrícula de propiedades contiene los valores de propiedad. Un cliente puede utilizar el cuadro de división del control de cuadrícula de propiedad para cambiar el ancho de la columna de valores.  
  
##  <a name="a-namegetpropertycounta--cmfcpropertygridctrlgetpropertycount"></a><a name="getpropertycount"></a>CMFCPropertyGridCtrl::GetPropertyCount  
 Recupera el número de propiedades de un control de cuadrícula de propiedades.  
  
```  
int GetPropertyCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de propiedades.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetrowheighta--cmfcpropertygridctrlgetrowheight"></a><a name="getrowheight"></a>CMFCPropertyGridCtrl::GetRowHeight  
 Recupera el alto de una fila en el control de cuadrícula de propiedades.  
  
```  
int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto de una fila.  
  
### <a name="remarks"></a>Comentarios  
 El alto de una fila es igual a la altura de la fuente actual más de 4 píxeles.  
  
##  <a name="a-namegetscrollbarctrla--cmfcpropertygridctrlgetscrollbarctrl"></a><a name="getscrollbarctrl"></a>CMFCPropertyGridCtrl::GetScrollBarCtrl  
 Recupera un puntero a la barra de desplazamiento en el control de cuadrícula de propiedad.  
  
```  
virtual CScrollBar* GetScrollBarCtrl(int nBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nBar`  
 La orientación de la barra de desplazamiento, que debe ser `SB_VERT`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un objeto de barra de desplazamiento o `NULL` si no hay ninguna barra de desplazamiento o la orientación de la barra de desplazamiento es `SB_HORZ`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para obtener acceso directo a la barra de desplazamiento vertical.  
  
##  <a name="a-namegettextcolora--cmfcpropertygridctrlgettextcolor"></a><a name="gettextcolor"></a>CMFCPropertyGridCtrl::GetTextColor  
 Recupera el color que se utiliza para dibujar el texto de los elementos de propiedad en el control de cuadrícula de propiedad actual.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el color que el marco de trabajo que se usa para dibujar el primer plano del control de cuadrícula de propiedad actual. El [CMFCPropertyGridCtrl::GetBkColor](#getbkcolor) método recupera el color de fondo.  
  
##  <a name="a-namehittesta--cmfcpropertygridctrlhittest"></a><a name="hittest"></a>CMFCPropertyGridCtrl::HitTest  
 Recupera un puntero al objeto de propiedad que corresponde a un elemento de control de cuadrícula de propiedades, si es un punto especificado en el elemento. Este método también indica el área en el control de cuadrícula de propiedad que contiene el punto.  
  
```  
CMFCPropertyGridProperty* HitTest(
    CPoint pt,  
    CMFCPropertyGridProperty::ClickArea* pnArea=NULL,  
    BOOL bPropsOnly=FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Un punto en coordenadas de cliente.  
  
 [in, out] `pnArea`  
 Un puntero a un `ClickArea` variable. Cuando se devuelve este método, la variable indica la *área propiedad* que contiene el punto especificado. Para obtener más información acerca de un área de la propiedad, vea la sección Comentarios.  
  
 [in] `bPropsOnly`  
 `TRUE`Para probar el área de propiedad; `FALSE` para probar el *área Descripción* si el punto especificado no está en el área de la propiedad. El valor predeterminado es `FALSE`. Para obtener más información sobre el área de descripción, vea la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el `bPropsOnly` parámetro es `TRUE` y el punto especificado está en el área de la propiedad, el valor devuelto es un puntero al objeto de propiedad correspondiente. Además, el `pnArea` parámetro se establece en el área en particular que contiene el punto especificado. De lo contrario, el valor devuelto es `NULL` y `pnArea` parámetro no se modifica.  
  
 Si el `bPropsOnly` parámetro es `FALSE`, el valor devuelto es siempre `NULL`. Sin embargo, si el punto especificado está en el área de descripción, la `pnArea` parámetro está establecido en `CMFCPropertyGridProperty::ClickDescription`.  
  
### <a name="remarks"></a>Comentarios  
 El término *área propiedad* hace referencia a uno de lo nombre y valor, o expandir las áreas del cuadro de un elemento de control de cuadrícula de propiedades. El *área Descripción* es la zona en la parte inferior de un control de cuadrícula de propiedades. Al hacer clic en un elemento de control de cuadrícula de propiedades, el área de descripción muestra una descripción de la propiedad correspondiente.  
  
 Este método establece el valor de la variable que la `pnArea` parámetro señala a. En la tabla siguiente se enumera los valores posibles y áreas correspondientes.  
  
|Valor|Área|  
|-----------|----------|  
|`ClickArea::ClickExpandBox`|Propiedad expanda control de cuadro.|  
|`ClickArea::ClickName`|Nombre de la propiedad.|  
|`ClickArea::ClickValue`|Valor de propiedad.|  
|`CMFCPropertyGridProperty::ClickDescription`|Área de descripción de control de cuadrícula de propiedades.|  
  
##  <a name="a-nameinita--cmfcpropertygridctrlinit"></a><a name="init"></a>CMFCPropertyGridCtrl::Init  
 Llamado por el marco para inicializar un control de cuadrícula de propiedades.  
  
```  
virtual void Init();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinitheadera--cmfcpropertygridctrlinitheader"></a><a name="initheader"></a>CMFCPropertyGridCtrl::InitHeader  
 Inicializa el interno [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que utiliza el marco de trabajo para mostrar el control de cuadrícula de propiedad actuales del objeto.  
  
```  
virtual void InitHeader();
```  
  
##  <a name="a-nameisalphabeticmodea--cmfcpropertygridctrlisalphabeticmode"></a><a name="isalphabeticmode"></a>CMFCPropertyGridCtrl::IsAlphabeticMode  
 Indica si un control de cuadrícula de propiedades está en modo alfabético.  
  
```  
BOOL IsAlphabeticMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de cuadrícula de propiedad está en modo alfabético; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de cuadrícula de propiedad está en modo alfabético, todas las propiedades se ordenan alfabéticamente por sus nombres. De lo contrario, las propiedades se agrupan en sus nodos principales.  
  
 Utilice la [CMFCPropertyGridCtrl::SetAlphabeticMode](#setalphabeticmode) método para habilitar o deshabilitar el modo de carácter alfabético.  
  
##  <a name="a-nameisalwaysshowusertooltipa--cmfcpropertygridctrlisalwaysshowusertooltip"></a><a name="isalwaysshowusertooltip"></a>CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAlwaysShowUserToolTip() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdescriptionareaa--cmfcpropertygridctrlisdescriptionarea"></a><a name="isdescriptionarea"></a>CMFCPropertyGridCtrl::IsDescriptionArea  
 Indica si se muestra el área de descripción del control de cuadrícula de propiedad.  
  
```  
BOOL IsDescriptionArea() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra el área de descripción; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea) método para ocultar o mostrar el área de descripción.  
  
##  <a name="a-nameisgroupnamefullwidtha--cmfcpropertygridctrlisgroupnamefullwidth"></a><a name="isgroupnamefullwidth"></a>CMFCPropertyGridCtrl::IsGroupNameFullWidth  
 Indica si cada nombre de grupo se muestra en el ancho del control de cuadrícula de propiedad actual.  
  
```  
BOOL IsGroupNameFullWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestran los nombres de grupo en el ancho del control de cuadrícula de propiedad; `FALSE` si los nombres de grupo se truncan por la columna de la derecha (valor) del control.  
  
### <a name="remarks"></a>Comentarios  
 Un *grupo* es una colección de propiedades relacionadas en un control de cuadrícula de propiedades. Si el control se muestre de forma jerárquica, el *nombre del grupo de* se muestra como título de una categoría de la fila superior del grupo.  
  
##  <a name="a-nameisheaderctrla--cmfcpropertygridctrlisheaderctrl"></a><a name="isheaderctrl"></a>CMFCPropertyGridCtrl::IsHeaderCtrl  
 Indica si se muestra el control de encabezado.  
  
```  
BOOL IsHeaderCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra el control de encabezado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::EnableHeaderCtrl](#enableheaderctrl) método para ocultar o mostrar el control de encabezado.  
  
##  <a name="a-nameismarkmodifiedpropertiesa--cmfcpropertygridctrlismarkmodifiedproperties"></a><a name="ismarkmodifiedproperties"></a>CMFCPropertyGridCtrl::IsMarkModifiedProperties  
 Indica cómo el control de cuadrícula de propiedades muestra las propiedades modificadas.  
  
```  
BOOL IsMarkModifiedProperties() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estilo de negrita se utiliza para mostrar, modificar propiedades; `FALSE` si se utiliza el estilo normal para mostrar las propiedades modificadas.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisshowdragcontexta--cmfcpropertygridctrlisshowdragcontext"></a><a name="isshowdragcontext"></a>CMFCPropertyGridCtrl::IsShowDragContext  
 Indica si el marco de trabajo se vuelve a dibujar las columnas de nombre y valor del control de cuadrícula de propiedad actual cuando un usuario cambia el tamaño de las columnas.  
  
```  
BOOL IsShowDragContext() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo se vuelve a dibujar las columnas de nombre y valor durante una operación de cambio de tamaño; `FALSE` si el marco de trabajo se vuelve a dibujar las columnas una vez completada la operación de arrastre.  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede cambiar el tamaño de las columnas de nombre y valor de un control de cuadrícula de propiedades arrastrando la barra de división entre las columnas. Si se muestra el contexto de arrastre, las columnas de nombre y valor se cambia el tamaño mientras el usuario arrastra la barra de división. En caso contrario, se mueve la barra de división, pero las columnas no se vuelven a dibujar hasta que se complete la operación de arrastre.  
  
##  <a name="a-nameisvsdotnetlooka--cmfcpropertygridctrlisvsdotnetlook"></a><a name="isvsdotnetlook"></a>CMFCPropertyGridCtrl::IsVSDotNetLook  
 Indica si la apariencia del control de cuadrícula de propiedad es en el estilo de Visual Studio. NET.  
  
```  
BOOL IsVSDotNetLook() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de cuadrícula de propiedad es en el estilo de Visual Studio. NET; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::SetVSDotNetLook](#setvsdotnetlook) para establecer el control de cuadrícula de propiedad al estilo de Visual Studio. NET.  
  
##  <a name="a-namemarkmodifiedpropertiesa--cmfcpropertygridctrlmarkmodifiedproperties"></a><a name="markmodifiedproperties"></a>CMFCPropertyGridCtrl::MarkModifiedProperties  
 Especifica cómo mostrar las propiedades modificadas.  
  
```  
void MarkModifiedProperties(
    BOOL bMark=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMark`  
 `TRUE`para mostrar las propiedades de estilo negrita; modificadas `FALSE` para mostrar las propiedades modificadas en el estilo normal. El valor predeterminado es `TRUE`.  
  
 [in] `bRedraw`  
 `TRUE`Para volver a dibujar el control de cuadrícula de propiedad inmediatamente; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchangeselectiona--cmfcpropertygridctrlonchangeselection"></a><a name="onchangeselection"></a>CMFCPropertyGridCtrl::OnChangeSelection  
 Llamado por el marco de trabajo cuando se cambia la selección actual.  
  
```  
virtual void OnChangeSelection(
    CMFCPropertyGridProperty* pNewSel,   
    CMFCPropertyGridProperty* pOldSel);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pNewSel`|Puntero a la propiedad recién seleccionada.|  
|[in] `pOldSel`|Puntero a la propiedad seleccionada anteriormente.|  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método no hace nada.  
  
##  <a name="a-nameonclickbuttona--cmfcpropertygridctrlonclickbutton"></a><a name="onclickbutton"></a>CMFCPropertyGridCtrl::OnClickButton  
 Lo llama el marco de trabajo cuando se hace clic en un botón de la propiedad.  
  
```  
virtual void OnClickButton(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Un punto en coordenadas de cliente.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método actualiza el valor de propiedad actual.  
  
##  <a name="a-nameondrawbordera--cmfcpropertygridctrlondrawborder"></a><a name="ondrawborder"></a>CMFCPropertyGridCtrl::OnDrawBorder  
 Llamado por el marco para dibujar un borde alrededor de un control de cuadrícula de propiedad.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawdescriptiona--cmfcpropertygridctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCPropertyGridCtrl::OnDrawDescription  
 Llamado por el marco para dibujar el área de descripción y mostrar el texto de descripción.  
  
```  
virtual void OnDrawDescription(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica dónde se va a dibujar el área de descripción.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea) método para mostrar el área de descripción.  
  
##  <a name="a-nameondrawlista--cmfcpropertygridctrlondrawlist"></a><a name="ondrawlist"></a>CMFCPropertyGridCtrl::OnDrawList  
 Llamado por el marco de trabajo para mostrar la lista de propiedades en el control de cuadrícula de propiedades.  
  
```  
virtual void OnDrawList(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawpropertya--cmfcpropertygridctrlondrawproperty"></a><a name="ondrawproperty"></a>CMFCPropertyGridCtrl::OnDrawProperty  
 Llamado por el marco de trabajo para mostrar una propiedad.  
  
```  
virtual int OnDrawProperty(
    CDC* pDC,  
    CMFCPropertyGridProperty* pProp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pProp`  
 Puntero a un objeto de propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonpropertychangeda--cmfcpropertygridctrlonpropertychanged"></a><a name="onpropertychanged"></a>CMFCPropertyGridCtrl::OnPropertyChanged  
 Llamado por el marco de trabajo cuando se cambia el valor de una propiedad.  
  
```  
virtual void OnPropertyChanged(CMFCPropertyGridProperty* pProp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a un objeto de la propiedad cuyo valor ha cambiado.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método envía el [AFX_WM_PROPERTY_CHANGED](../../mfc/reference/afx-messages.md) mensaje al propietario del control de cuadrícula de propiedad.  
  
##  <a name="a-nameonselectcomboa--cmfcpropertygridctrlonselectcombo"></a><a name="onselectcombo"></a>CMFCPropertyGridCtrl::OnSelectCombo  
 Lo llama el marco de trabajo cuando se selecciona una propiedad que contiene un control de cuadro combinado.  
  
```  
void OnSelectCombo();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremovealla--cmfcpropertygridctrlremoveall"></a><a name="removeall"></a>CMFCPropertyGridCtrl::RemoveAll  
 Quita todos los objetos de propiedad de un control de cuadrícula de propiedades.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameresetoriginalvaluesa--cmfcpropertygridctrlresetoriginalvalues"></a><a name="resetoriginalvalues"></a>CMFCPropertyGridCtrl::ResetOriginalValues  
 Restaura los valores originales de todas las propiedades.  
  
```  
void ResetOriginalValues(BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bRedraw`  
 `TRUE`Para volver a dibujar la lista de propiedades; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetalphabeticmodea--cmfcpropertygridctrlsetalphabeticmode"></a><a name="setalphabeticmode"></a>CMFCPropertyGridCtrl::SetAlphabeticMode  
 Establece o restablece el modo de carácter alfabético.  
  
```  
void SetAlphabeticMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`Para establecer el modo alfabético; `FALSE` modo alfabético de restablecimiento. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de cuadrícula de propiedad está en modo alfabético, el control ordena todas las propiedades que contiene su nombre de propiedad.  
  
##  <a name="a-namesetboollabelsa--cmfcpropertygridctrlsetboollabels"></a><a name="setboollabels"></a>CMFCPropertyGridCtrl::SetBoolLabels  
 Especifica el texto de las etiquetas de tipo Boolean.  
  
```  
void SetBoolLabels(
    LPCTSTR lpszTrue,  
    LPCTSTR lpszFalse);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszTrue`  
 Cadena de texto para mostrar el valor booleano true.  
  
 [in] `lpszFalse`  
 Cadena de texto para mostrar el valor booleano false.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcursela--cmfcpropertygridctrlsetcursel"></a><a name="setcursel"></a>CMFCPropertyGridCtrl::SetCurSel  
 Selecciona una propiedad de un control de cuadrícula de propiedades.  
  
```  
void SetCurSel(
    CMFCPropertyGridProperty* pProp,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pProp`  
 Puntero a un objeto de propiedad.  
  
 [in] `bRedraw`  
 `TRUE`Para volver a dibujar el control de cuadrícula de propiedad inmediatamente; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para cancelar la selección del elemento actual en el control de cuadrícula de propiedad y, a continuación, seleccione el elemento que corresponde a la propiedad especificada.  
  
##  <a name="a-namesetcustomcolorsa--cmfcpropertygridctrlsetcustomcolors"></a><a name="setcustomcolors"></a>CMFCPropertyGridCtrl::SetCustomColors  
 Especifica los colores personalizados para distintos elementos del control de cuadrícula de propiedad.  
  
```  
void SetCustomColors(
    COLORREF clrBackground,  
    COLORREF clrText,  
    COLORREF clrGroupBackground,  
    COLORREF clrGroupText,  
    COLORREF clrDescriptionBackground,  
    COLORREF clrDescriptionText,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrBackground`  
 El color de fondo de los valores de propiedad.  
  
 [in] `clrText`  
 El color de los nombres de propiedad y el texto del valor de propiedad.  
  
 [in] `clrGroupBackground`  
 El color de fondo de un grupo de propiedades.  
  
 [in] `clrGroupText`  
 El nuevo color de texto de grupo de propiedades.  
  
 [in] `clrDescriptionBackground`  
 El color de fondo del área de descripción.  
  
 [in] `clrDescriptionText`  
 El color del texto en el área de descripción.  
  
 [in] `clrLine`  
 El color de las líneas que se dibujan entre las propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Para cualquier parámetro, especifique el `((COLORREF)-1)` valor para utilizar el color predeterminado para ese elemento del control de cuadrícula de propiedad de color.  
  
 Para personalizar la apariencia de una propiedad concreta, derive una clase de la [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md) de clase y, a continuación, reemplace el [CMFCPropertyGridProperty::OnDrawName](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawname), [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue), [CMFCPropertyGridProperty::OnDrawExpandBox](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawexpandbox), y [CMFCPropertyGridProperty::OnDrawButton](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawbutton) métodos.  
  
##  <a name="a-namesetdescriptionrowsa--cmfcpropertygridctrlsetdescriptionrows"></a><a name="setdescriptionrows"></a>CMFCPropertyGridCtrl::SetDescriptionRows  
 Especifica el número de filas que se muestran en la sección de descripción del control de cuadrícula de propiedad actual.  
  
```  
void SetDescriptionRows(int nDescRows);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nDescRows`  
 El número de filas que se muestran en la descripción de propiedad.  
  
##  <a name="a-namesetgroupnamefullwidtha--cmfcpropertygridctrlsetgroupnamefullwidth"></a><a name="setgroupnamefullwidth"></a>CMFCPropertyGridCtrl::SetGroupNameFullWidth  
 Especifica si se muestra el ancho completo del nombre de categoría de un grupo de propiedades en el control de cuadrícula de propiedad actual.  
  
```  
void SetGroupNameFullWidth(
    BOOL bGroupNameFullWidth = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bGroupNameFullWidth`  
 `TRUE`para mostrar el ancho completo del nombre de categoría, independientemente del ancho de la columna de nombre de propiedad. `FALSE`Para limitar el ancho del nombre de categoría para el ancho de la columna de nombre de propiedad. El valor predeterminado es `TRUE`.  
  
 [in] `bRedraw`  
 `TRUE`Para actualizar el control de cuadrícula de propiedad inmediatamente; `FALSE` actualizar el control cuando la próxima volver a dibujar el evento se produce. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El control de cuadrícula de propiedad consta de un tamaño variable *nombre de propiedad* columna y un *valor de la propiedad* columna. Al final de la columna de nombre también es el inicio de la columna de valor. Para cambiar el tamaño de las columnas, arrastre el borde entre las columnas.  
  
 Los términos *nombre del grupo de* y *nombre de categoría* se usan indistintamente en este método. Se muestra el nombre de categoría en una fila que se dirige a un conjunto de valores y propiedades relacionadas. Este método especifica si el ancho de la columna de nombre de propiedad también especifica el ancho del nombre de la categoría mostrada.  
  
##  <a name="a-namesetlistdelimitera--cmfcpropertygridctrlsetlistdelimiter"></a><a name="setlistdelimiter"></a>CMFCPropertyGridCtrl::SetListDelimiter  
 Define un carácter que se utiliza como un delimitador en una lista de valores de propiedad.  
  
```  
void SetListDelimiter(TCHAR c);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `c`  
 Un carácter que se va a actuar como un delimitador.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para definir un carácter delimitador en una lista de valores de propiedad que se usan en el [CMFCPropertyGridProperty::CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#cmfcpropertygridproperty) constructor. En el constructor, establezca el `bIsValueList` parámetro `TRUE`.  
  
 De forma predeterminada, el [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl) constructor establece el carácter delimitador para coma (',').  
  
##  <a name="a-namesetshowdragcontexta--cmfcpropertygridctrlsetshowdragcontext"></a><a name="setshowdragcontext"></a>CMFCPropertyGridCtrl::SetShowDragContext  
 Especifica si el marco de trabajo se vuelve a dibujar las columnas de nombre y valor del control de cuadrícula de propiedad actual cuando un usuario cambia el tamaño de las columnas.  
  
```  
void SetShowDragContext(BOOL bShowDragContext = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShowDragContext`  
 `TRUE`Para volver a dibujar las columnas de nombre y valor durante una operación de cambio de tamaño; `FALSE` para volver a dibujar las columnas una vez completada la operación de arrastre. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede cambiar el tamaño de las columnas de nombre y valor de un control de cuadrícula de propiedades arrastrando la barra de división entre las columnas. Si se muestra el contexto de arrastre, las columnas de nombre y valor se cambia el tamaño mientras el usuario arrastra la barra de división. En caso contrario, se mueve la barra de división, pero las columnas no se vuelven a dibujar hasta que se complete la operación de arrastre.  
  
##  <a name="a-namesetvsdotnetlooka--cmfcpropertygridctrlsetvsdotnetlook"></a><a name="setvsdotnetlook"></a>CMFCPropertyGridCtrl::SetVSDotNetLook  
 Establece la apariencia del control de cuadrícula de propiedad en el estilo que se utiliza en Visual Studio. NET.  
  
```  
void SetVSDotNetLook(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`Para establecer el control de cuadrícula de propiedades en el estilo que se utiliza en Visual Studio. NET; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameupdatecolora--cmfcpropertygridctrlupdatecolor"></a><a name="updatecolor"></a>CMFCPropertyGridCtrl::UpdateColor  
 Establece el valor de color de la propiedad de color seleccionado.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Este método valida en modo de depuración, si la propiedad del control de cuadrícula de propiedad seleccionada actualmente no es una propiedad de color.  
  
##  <a name="a-namevalidateitemdataa--cmfcpropertygridctrlvalidateitemdata"></a><a name="validateitemdata"></a>CMFCPropertyGridCtrl::ValidateItemData  
 Llamado por el marco para validar los datos de propiedad.  
  
```  
virtual BOOL ValidateItemData(CMFCPropertyGridProperty* pProp);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pProp`|Puntero a una propiedad. Este parámetro no se utiliza.|  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCPropertyGridCtrl::EndEditItem](#endedititem) método llama a este método para validar los datos. De forma predeterminada, este método no utiliza su `pProp` parámetro y su valor devuelto es siempre `TRUE`.  
  
 Si invalida este método, devolver `TRUE` si los datos de la propiedad especificada están válidos. De lo contrario, devuelve `FALSE`, en cuyo caso el marco de trabajo no actualiza la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

