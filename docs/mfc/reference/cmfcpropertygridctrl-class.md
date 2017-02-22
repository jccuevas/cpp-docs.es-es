---
title: "CMFCPropertyGridCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridCtrl class"
  - "CMFCPropertyGridCtrl::accHitTest method"
  - "CMFCPropertyGridCtrl::accLocation method"
  - "CMFCPropertyGridCtrl::get_accChild method"
  - "CMFCPropertyGridCtrl::get_accDefaultAction method"
  - "CMFCPropertyGridCtrl::get_accDescription method"
  - "CMFCPropertyGridCtrl::get_accName method"
  - "CMFCPropertyGridCtrl::get_accRole method"
  - "CMFCPropertyGridCtrl::get_accState method"
  - "CMFCPropertyGridCtrl::get_accValue method"
  - "CMFCPropertyGridCtrl::PreTranslateMessage method"
ms.assetid: 95877cae-2311-4a2a-9031-0c8c3cf0a5f9
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCPropertyGridCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Admite un control de cuadrícula de propiedades editables que puede mostrar propiedades en orden alfabético o jerárquico.  
  
## Sintaxis  
  
```  
class CMFCPropertyGridCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](../Topic/CMFCPropertyGridCtrl::CMFCPropertyGridCtrl.md)|Crea un objeto `CMFCPropertyGridCtrl`.|  
|`CMFCPropertyGridCtrl::~CMFCPropertyGridCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCPropertyGridCtrl::accHitTest`|Llamado por el marco para recuperar el elemento secundario o el objeto secundario en un punto determinado de la pantalla.  \(Reemplaza [CWnd::accHitTest](../Topic/CWnd::accHitTest.md).\)|  
|`CMFCPropertyGridCtrl::accLocation`|Llamado por el marco para recuperar la ubicación actual de la pantalla del objeto especificado.  \(Reemplaza [CWnd::accLocation](../Topic/CWnd::accLocation.md).\)|  
|[CMFCPropertyGridCtrl::accSelect](../Topic/CMFCPropertyGridCtrl::accSelect.md)|Llamado por el marco para modificar la selección o para mover el foco de teclado del objeto especificado.  \(Reemplaza [CWnd::accSelect](../Topic/CWnd::accSelect.md).\)|  
|[CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md)|agrega una nueva propiedad a un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::AlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::AlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::CloseColorPopup](../Topic/CMFCPropertyGridCtrl::CloseColorPopup.md)|Cierre el cuadro de diálogo de selección de color.|  
|[CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md)|Crea un control de cuadrícula de propiedades y lo asocia al objeto de control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::DeleteProperty](../Topic/CMFCPropertyGridCtrl::DeleteProperty.md)|Elimina la propiedad especificada del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::DrawControlBarColors](../Topic/CMFCPropertyGridCtrl::DrawControlBarColors.md)||  
|[CMFCPropertyGridCtrl::EnableDescriptionArea](../Topic/CMFCPropertyGridCtrl::EnableDescriptionArea.md)|Habilita o deshabilita el área de descripción que se muestra bajo la lista de propiedades.|  
|[CMFCPropertyGridCtrl::EnableHeaderCtrl](../Topic/CMFCPropertyGridCtrl::EnableHeaderCtrl.md)|Habilita o deshabilita el control de encabezado en la parte superior del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::EnsureVisible](../Topic/CMFCPropertyGridCtrl::EnsureVisible.md)|Desplaza un control de cuadrícula de propiedades y expanda los elementos de propiedad hasta que la propiedad especificada sea visible.|  
|[CMFCPropertyGridCtrl::ExpandAll](../Topic/CMFCPropertyGridCtrl::ExpandAll.md)|Expande o contrae todos los nodos del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::FindItemByData](../Topic/CMFCPropertyGridCtrl::FindItemByData.md)|Recupera la propiedad que está asociado a un valor definido por el usuario de `DWORD` .|  
|`CMFCPropertyGridCtrl::get_accChild`|Llamado por el marco para recuperar la dirección de una interfaz de `IDispatch` para el elemento secundario especificado.  \(Reemplaza [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md).\)|  
|[CMFCPropertyGridCtrl::get\_accChildCount](../Topic/CMFCPropertyGridCtrl::get_accChildCount.md)|Llamado por el marco para recuperar el número de elementos secundarios que pertenecen a este objeto.  \(Reemplaza [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md).\)|  
|`CMFCPropertyGridCtrl::get_accDefaultAction`|Llamado por el marco para recuperar una cadena que describe la acción predeterminada del objeto.  \(Reemplaza [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md).\)|  
|`CMFCPropertyGridCtrl::get_accDescription`|Llamado por el marco para recuperar una cadena que describe la apariencia visual del objeto especificado.  \(Reemplaza [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md).\)|  
|[CMFCPropertyGridCtrl::get\_accFocus](../Topic/CMFCPropertyGridCtrl::get_accFocus.md)|Llamado por el marco para recuperar el objeto que tiene el foco de teclado.  \(Reemplaza [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md).\)|  
|[CMFCPropertyGridCtrl::get\_accHelp](../Topic/CMFCPropertyGridCtrl::get_accHelp.md)|Llamado por el marco para recuperar la cadena de la propiedad de `Help` de un objeto.  \(Reemplaza [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md).\)|  
|[CMFCPropertyGridCtrl::get\_accHelpTopic](../Topic/CMFCPropertyGridCtrl::get_accHelpTopic.md)|Llamado por el marco para recuperar la ruta de acceso completa del archivo de `WinHelp`asociado al objeto especificado y el identificador del tema correspondiente dentro de ese archivo.  \(Reemplaza [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md).\)|  
|[CMFCPropertyGridCtrl::get\_accKeyboardShortcut](../Topic/CMFCPropertyGridCtrl::get_accKeyboardShortcut.md)|Llamado por el marco para recuperar la tecla de método abreviado o la tecla de acceso del objeto especificado.  \(Reemplaza [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md).\)|  
|`CMFCPropertyGridCtrl::get_accName`|Llamado por el marco para recuperar el nombre del objeto especificado.  \(Reemplaza [CWnd::get\_accName](../Topic/CWnd::get_accName.md).\)|  
|`CMFCPropertyGridCtrl::get_accRole`|Llamado por el marco para recuperar la información que describe el rol del objeto especificado.  \(Reemplaza [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md).\)|  
|[CMFCPropertyGridCtrl::get\_accSelection](../Topic/CMFCPropertyGridCtrl::get_accSelection.md)|Llamado por el marco para recuperar los elementos secundarios de este objeto.  \(Reemplaza [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md).\)|  
|`CMFCPropertyGridCtrl::get_accState`|Llamado por el marco para recuperar el estado actual del objeto especificado.  \(Reemplaza [CWnd::get\_accState](../Topic/CWnd::get_accState.md).\)|  
|`CMFCPropertyGridCtrl::get_accValue`|Llamado por el marco para recuperar el valor del objeto especificado.  \(Reemplaza [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md).\)|  
|[CMFCPropertyGridCtrl::GetBkColor](../Topic/CMFCPropertyGridCtrl::GetBkColor.md)|Recupera el color de fondo del control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::GetBoldFont](../Topic/CMFCPropertyGridCtrl::GetBoldFont.md)|Recuperar la fuente de Windows que de texto en el control de cuadrícula de propiedades actual en estilo negrita.|  
|[CMFCPropertyGridCtrl::GetCurSel](../Topic/CMFCPropertyGridCtrl::GetCurSel.md)|recupera la propiedad actualmente seleccionado.|  
|[CMFCPropertyGridCtrl::GetCustomColors](../Topic/CMFCPropertyGridCtrl::GetCustomColors.md)|recupera los colores personalizados que son actualmente definido para los elementos de control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetDescriptionHeight](../Topic/CMFCPropertyGridCtrl::GetDescriptionHeight.md)|Recupera el alto de la descripción situada en la parte inferior del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetDescriptionRows](../Topic/CMFCPropertyGridCtrl::GetDescriptionRows.md)|Recupera el número de filas en el área de la descripción del control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::GetHeaderCtrl](../Topic/CMFCPropertyGridCtrl::GetHeaderCtrl.md)|Recupera el objeto interno de [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que el marco de trabajo usa para mostrar el control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::GetHeaderHeight](../Topic/CMFCPropertyGridCtrl::GetHeaderHeight.md)|Recupera el alto del encabezado del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetLeftColumnWidth](../Topic/CMFCPropertyGridCtrl::GetLeftColumnWidth.md)|Recupera el ancho de la columna izquierda del control de cuadrícula de propiedades actual, que contiene el nombre de cada propiedad.|  
|[CMFCPropertyGridCtrl::GetListRect](../Topic/CMFCPropertyGridCtrl::GetListRect.md)|Recupera el rectángulo delimitador del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetProperty](../Topic/CMFCPropertyGridCtrl::GetProperty.md)|Recupera un puntero al objeto de propiedad correspondiente al índice especificado de un elemento del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetPropertyColumnWidth](../Topic/CMFCPropertyGridCtrl::GetPropertyColumnWidth.md)|recupera el ancho actual de la columna que contiene valores de propiedad.|  
|[CMFCPropertyGridCtrl::GetPropertyCount](../Topic/CMFCPropertyGridCtrl::GetPropertyCount.md)|recupera el número de propiedades en un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetRowHeight](../Topic/CMFCPropertyGridCtrl::GetRowHeight.md)|recupera el alto de una fila en el control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::GetScrollBarCtrl](../Topic/CMFCPropertyGridCtrl::GetScrollBarCtrl.md)|Recupera un puntero al control de barra de desplazamiento en el control de cuadrícula de propiedades.  \(Reemplaza [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md).\)|  
|[CMFCPropertyGridCtrl::GetTextColor](../Topic/CMFCPropertyGridCtrl::GetTextColor.md)|Recupera el color del texto de los elementos de propiedad en el control de cuadrícula de propiedades actual.|  
|`CMFCPropertyGridCtrl::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCPropertyGridCtrl::HitTest](../Topic/CMFCPropertyGridCtrl::HitTest.md)|Recupera un puntero al objeto de la propiedad que corresponde a un elemento del control de cuadrícula de propiedades si un punto especificado está en el elemento.  este método también indica el área en el control de cuadrícula de propiedades que contiene el punto.|  
|[CMFCPropertyGridCtrl::InitHeader](../Topic/CMFCPropertyGridCtrl::InitHeader.md)|Inicializa el objeto interno de [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) que el marco de trabajo usa para mostrar el control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::IsAlphabeticMode](../Topic/CMFCPropertyGridCtrl::IsAlphabeticMode.md)|indica si un control de cuadrícula de propiedades está en modo alfabético.|  
|[CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::IsDescriptionArea](../Topic/CMFCPropertyGridCtrl::IsDescriptionArea.md)|Indica si el área de la descripción del control de cuadrícula de propiedades se muestra.|  
|[CMFCPropertyGridCtrl::IsGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::IsGroupNameFullWidth.md)|Indica si cada nombre de grupo de propiedades se muestra mediante el ancho del control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::IsHeaderCtrl](../Topic/CMFCPropertyGridCtrl::IsHeaderCtrl.md)|Indica si el control de encabezado se muestra.|  
|[CMFCPropertyGridCtrl::IsMarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::IsMarkModifiedProperties.md)|Indica cómo el control de cuadrícula de propiedades muestra las propiedades modificadas.|  
|[CMFCPropertyGridCtrl::IsShowDragContext](../Topic/CMFCPropertyGridCtrl::IsShowDragContext.md)|Indica si el marco dibuja de nuevo el nombre y columnas valor del control de cuadrícula de propiedades actual cuando un usuario cambia el tamaño de las columnas.|  
|[CMFCPropertyGridCtrl::IsVSDotNetLook](../Topic/CMFCPropertyGridCtrl::IsVSDotNetLook.md)|Indica si el aspecto del control de cuadrícula de propiedades está en el estilo que usa VS .NET.|  
|[CMFCPropertyGridCtrl::MarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::MarkModifiedProperties.md)|Especifica cómo mostrar propiedades modificadas.|  
|`CMFCPropertyGridCtrl::PreTranslateMessage`|Utiliza la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CMFCPropertyGridCtrl::RemoveAll](../Topic/CMFCPropertyGridCtrl::RemoveAll.md)|Quita todos los objetos de propiedad de un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::ResetOriginalValues](../Topic/CMFCPropertyGridCtrl::ResetOriginalValues.md)|restablece el valor original de todas las propiedades.|  
|[CMFCPropertyGridCtrl::SetAlphabeticMode](../Topic/CMFCPropertyGridCtrl::SetAlphabeticMode.md)|Obtiene o modo alfabético de los reinicios.|  
|[CMFCPropertyGridCtrl::SetBoolLabels](../Topic/CMFCPropertyGridCtrl::SetBoolLabels.md)|Especifica el texto de etiquetas boolean.|  
|[CMFCPropertyGridCtrl::SetCurSel](../Topic/CMFCPropertyGridCtrl::SetCurSel.md)|Seleccione una propiedad en un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::SetCustomColors](../Topic/CMFCPropertyGridCtrl::SetCustomColors.md)|Especifica los colores personalizados para los distintos elementos de control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::SetDescriptionRows](../Topic/CMFCPropertyGridCtrl::SetDescriptionRows.md)|Especifica el número de filas que se mostrarán en la sección de la descripción del control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::SetGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::SetGroupNameFullWidth.md)|Especifica si mostrar el ancho del nombre de categoría para un grupo de propiedades en el control de cuadrícula de propiedades actual.|  
|[CMFCPropertyGridCtrl::SetListDelimiter](../Topic/CMFCPropertyGridCtrl::SetListDelimiter.md)|Define un carácter que se utilice como delimitador en una lista de valores de propiedad.|  
|[CMFCPropertyGridCtrl::SetShowDragContext](../Topic/CMFCPropertyGridCtrl::SetShowDragContext.md)|Especifica si el marco dibuja de nuevo el nombre y columnas valor del control de cuadrícula de propiedades actual cuando un usuario cambia el tamaño de las columnas.|  
|[CMFCPropertyGridCtrl::SetVSDotNetLook](../Topic/CMFCPropertyGridCtrl::SetVSDotNetLook.md)|Establece la apariencia del control de cuadrícula de propiedades de estilo que se utiliza en VS .NET.|  
|[CMFCPropertyGridCtrl::UpdateColor](../Topic/CMFCPropertyGridCtrl::UpdateColor.md)|Establece el valor de color de la propiedad color seleccionado actualmente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::AdjustLayout](../Topic/CMFCPropertyGridCtrl::AdjustLayout.md)|Dibuja de nuevo el control de cuadrícula de propiedades y sus propiedades.|  
|[CMFCPropertyGridCtrl::CompareProps](../Topic/CMFCPropertyGridCtrl::CompareProps.md)|Llamado por el control de cuadrícula de propiedades para ordenar propiedades.|  
|[CMFCPropertyGridCtrl::EditItem](../Topic/CMFCPropertyGridCtrl::EditItem.md)|Llamado por el marco cuando el usuario inicia para modificar una propiedad.|  
|[CMFCPropertyGridCtrl::EndEditItem](../Topic/CMFCPropertyGridCtrl::EndEditItem.md)|Llamado por el marco cuando el usuario detiene el modificar de una propiedad.|  
|[CMFCPropertyGridCtrl::Init](../Topic/CMFCPropertyGridCtrl::Init.md)|Llamado por el marco para inicializar un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::OnChangeSelection](../Topic/CMFCPropertyGridCtrl::OnChangeSelection.md)|Llamado por el marco cuando cambia la selección actual.|  
|[CMFCPropertyGridCtrl::OnClickButton](../Topic/CMFCPropertyGridCtrl::OnClickButton.md)|Llamado por el marco cuando se hace clic en un botón de la propiedad.|  
|[CMFCPropertyGridCtrl::OnDrawBorder](../Topic/CMFCPropertyGridCtrl::OnDrawBorder.md)|Llamado por el marco para dibujar un borde alrededor de un control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::OnDrawDescription](../Topic/CMFCPropertyGridCtrl::OnDrawDescription.md)|Llamado por el marco para dibujar el área de descripción y mostrar el texto de la descripción.|  
|[CMFCPropertyGridCtrl::OnDrawList](../Topic/CMFCPropertyGridCtrl::OnDrawList.md)|Llamado por el marco para mostrar la lista de propiedades del control de cuadrícula de propiedades.|  
|[CMFCPropertyGridCtrl::OnDrawProperty](../Topic/CMFCPropertyGridCtrl::OnDrawProperty.md)|Llamado por el marco para mostrar una propiedad.|  
|[CMFCPropertyGridCtrl::OnPropertyChanged](../Topic/CMFCPropertyGridCtrl::OnPropertyChanged.md)|Llamado por el marco cuando el valor de una propiedad cambia.|  
|[CMFCPropertyGridCtrl::OnSelectCombo](../Topic/CMFCPropertyGridCtrl::OnSelectCombo.md)|Llamado por el marco cuando una propiedad que contiene un control combobox está seleccionado.|  
|[CMFCPropertyGridCtrl::ValidateItemData](../Topic/CMFCPropertyGridCtrl::ValidateItemData.md)|Llamado por el marco para validar datos de propiedad.|  
  
## Comentarios  
 Muestra de clase de `CMFCPropertyGridCtrl` un control de cuadrícula de propiedades con las propiedades modificables derivadas de la clase de [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md) .  cada propiedad puede representar un tipo y puede contener subelementos.  El control de cuadrícula de propiedades admite un área de tamaño variable en la parte inferior que puede mostrar la descripción de una propiedad seleccionada.  
  
 Para utilizar un control de cuadrícula de propiedades, cree un objeto de `CMFCPropertyGridCtrl` y llame al método de [CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md) .  utilice el método de [CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md) para agregar propiedades a la lista.  
  
## Propiedades de selección  
 En lugar de representar un valor, un elemento de propiedad puede iniciar un cuadro de diálogo que permite al usuario seleccionar color, un archivo, o a una fuente.  
  
 La tabla siguiente se muestran cuatro tipos de propiedad de selección:  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)|Una propiedad de uso general que se utiliza para especificar el valor de cadenas, valores booleanos, fechas y así sucesivamente.|  
|[CMFCPropertyGridColorProperty Class](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)|Una propiedad que se utiliza para seleccionar un valor de color.|  
|[CMFCPropertyGridFileProperty Class](../../mfc/reference/cmfcpropertygridfileproperty-class.md)|Una propiedad que se utiliza para seleccionar un archivo.|  
|[CMFCPropertyGridFontProperty Class](../../mfc/reference/cmfcpropertygridfontproperty-class.md)|Una propiedad que se utiliza para seleccionar una fuente.|  
  
## Ilustraciones  
 Las ilustraciones siguientes describen un control de cuadrícula de propiedades que muestre propiedades de dos maneras.  La primera ilustración muestra propiedades jerárquico y la segunda muestra propiedades alfabéticamente.  
  
 ![Lista de propiedades PropertySheet](../../mfc/reference/media/proplist.png "PropList")  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de control de cuadrícula de propiedades mediante varios métodos en la clase de `CMFCPropertyGridCtrl` .  El ejemplo muestra cómo habilitar el control de encabezado, permite el área de descripción, y establece la apariencia del control de cuadrícula de propiedades.  El ejemplo también se muestra cómo establecer el modo alfabético para el control por el que el control ordenar todas las propiedades que contiene el nombre de propiedad, y cómo establecer los colores personalizados para los diferentes elementos del control de cuadrícula de propiedades.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#14](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#16](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#20](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#21](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_4.cpp)]  
[!code-cpp[NVC_MFC_NewControls#24](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_5.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxpropertygridctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)