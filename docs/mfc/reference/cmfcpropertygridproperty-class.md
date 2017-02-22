---
title: "CMFCPropertyGridProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridProperty class"
ms.assetid: 36f3fabe-0efe-468b-8a0b-5a7956db38a2
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCPropertyGridProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un objeto de `CMFCPropertyGridProperty` representa un elemento de un control de lista de propiedades.  
  
## Sintaxis  
  
```  
class CMFCPropertyGridProperty : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridProperty::CMFCPropertyGridProperty](../Topic/CMFCPropertyGridProperty::CMFCPropertyGridProperty.md)|Crea un objeto `CMFCPropertyGridProperty`.|  
|`CMFCPropertyGridProperty::~CMFCPropertyGridProperty`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridProperty::AddOption](../Topic/CMFCPropertyGridProperty::AddOption.md)|Agrega un nuevo elemento de lista a un control de lista de propiedades.|  
|[CMFCPropertyGridProperty::AddSubItem](../Topic/CMFCPropertyGridProperty::AddSubItem.md)|agrega un elemento secundario a una propiedad.|  
|[CMFCPropertyGridProperty::AdjustButtonRect](../Topic/CMFCPropertyGridProperty::AdjustButtonRect.md)|Llamado por el control de lista de la propiedad parent para indicar a una propiedad que cambie el tamaño del rectángulo delimitador de un botón incrustado.|  
|[CMFCPropertyGridProperty::AdjustInPlaceEditRect](../Topic/CMFCPropertyGridProperty::AdjustInPlaceEditRect.md)|Recupera los límites del cuadro de texto y el control de botón opcional de giro que se utilizan para establecer un valor de propiedad.|  
|[CMFCPropertyGridProperty::AllowEdit](../Topic/CMFCPropertyGridProperty::AllowEdit.md)|Crea una propiedad modificable o de sólo lectura.|  
|[CMFCPropertyGridProperty::CreateInPlaceEdit](../Topic/CMFCPropertyGridProperty::CreateInPlaceEdit.md)|Llamado por el marco para crear un control modificable para una propiedad.|  
|[CMFCPropertyGridProperty::CreateSpinControl](../Topic/CMFCPropertyGridProperty::CreateSpinControl.md)|Llamado por el marco para crear un control de botón modificable de número.|  
|[CMFCPropertyGridProperty::Enable](../Topic/CMFCPropertyGridProperty::Enable.md)|Habilita o deshabilita una propiedad.|  
|[CMFCPropertyGridProperty::EnableSpinControl](../Topic/CMFCPropertyGridProperty::EnableSpinControl.md)|Habilita o deshabilita un control de botón de giro que se utiliza para modificar un valor de propiedad.|  
|[CMFCPropertyGridProperty::Expand](../Topic/CMFCPropertyGridProperty::Expand.md)|Expande o contrae una propiedad que contiene sub\- propiedades.|  
|[CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)|Da formato a la representación de texto de un valor de propiedad.|  
|[CMFCPropertyGridProperty::GetData](../Topic/CMFCPropertyGridProperty::GetData.md)|Recupera un valor de `DWORD` que está asociado a una propiedad.|  
|[CMFCPropertyGridProperty::GetDescription](../Topic/CMFCPropertyGridProperty::GetDescription.md)|recupera una descripción de la propiedad.|  
|[CMFCPropertyGridProperty::GetExpandedSubItems](../Topic/CMFCPropertyGridProperty::GetExpandedSubItems.md)|Recupera el número de sub\- elementos expandida.|  
|[CMFCPropertyGridProperty::GetHierarchyLevel](../Topic/CMFCPropertyGridProperty::GetHierarchyLevel.md)|Recupera el índice de base cero del nivel de la jerarquía de la propiedad.|  
|[CMFCPropertyGridProperty::GetName](../Topic/CMFCPropertyGridProperty::GetName.md)|recupera el nombre de la propiedad.|  
|[CMFCPropertyGridProperty::GetNameTooltip](../Topic/CMFCPropertyGridProperty::GetNameTooltip.md)|Llamado por el marco para mostrar el nombre de la propiedad en una información sobre herramientas.|  
|[CMFCPropertyGridProperty::GetOption](../Topic/CMFCPropertyGridProperty::GetOption.md)|Recupera el texto de la opción especificada en un índice.|  
|[CMFCPropertyGridProperty::GetOptionCount](../Topic/CMFCPropertyGridProperty::GetOptionCount.md)|Recupera el número de opciones que pertenecen a una propiedad.|  
|[CMFCPropertyGridProperty::GetOriginalValue](../Topic/CMFCPropertyGridProperty::GetOriginalValue.md)|Recupera el valor inicial de la propiedad actual.|  
|[CMFCPropertyGridProperty::GetParent](../Topic/CMFCPropertyGridProperty::GetParent.md)|recupera un puntero a una propiedad parent.|  
|[CMFCPropertyGridProperty::GetRect](../Topic/CMFCPropertyGridProperty::GetRect.md)|Recupera el rectángulo delimitador de una propiedad.|  
|[CMFCPropertyGridProperty::GetSubItem](../Topic/CMFCPropertyGridProperty::GetSubItem.md)|Recupera una sub\-propiedad identificada por un índice cero\-basado.|  
|[CMFCPropertyGridProperty::GetSubItemsCount](../Topic/CMFCPropertyGridProperty::GetSubItemsCount.md)|recupera el número de sub\-elementos.|  
|`CMFCPropertyGridProperty::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCPropertyGridProperty::GetValue](../Topic/CMFCPropertyGridProperty::GetValue.md)|recupera un valor de propiedad.|  
|[CMFCPropertyGridProperty::GetValueTooltip](../Topic/CMFCPropertyGridProperty::GetValueTooltip.md)|Llamado por el marco para recuperar la representación de texto del valor de propiedad que se muestra en una información sobre herramientas.|  
|[CMFCPropertyGridProperty::HitTest](../Topic/CMFCPropertyGridProperty::HitTest.md)|Señala la propiedad se oponen que corresponde al elemento de la lista de propiedades correspondiente a un punto.|  
|[CMFCPropertyGridProperty::IsAllowEdit](../Topic/CMFCPropertyGridProperty::IsAllowEdit.md)|Indica si una propiedad se puede modificar.|  
|[CMFCPropertyGridProperty::IsEnabled](../Topic/CMFCPropertyGridProperty::IsEnabled.md)|indica si una propiedad está habilitada o deshabilitada.|  
|[CMFCPropertyGridProperty::IsExpanded](../Topic/CMFCPropertyGridProperty::IsExpanded.md)|Indica si una propiedad se expande o contrae.|  
|[CMFCPropertyGridProperty::IsGroup](../Topic/CMFCPropertyGridProperty::IsGroup.md)|Indica si la propiedad actual representa un grupo.|  
|[CMFCPropertyGridProperty::IsInPlaceEditing](../Topic/CMFCPropertyGridProperty::IsInPlaceEditing.md)|Indica si la propiedad actual es modificable.|  
|[CMFCPropertyGridProperty::IsModified](../Topic/CMFCPropertyGridProperty::IsModified.md)|indica si la propiedad actual está modificada.|  
|[CMFCPropertyGridProperty::IsParentExpanded](../Topic/CMFCPropertyGridProperty::IsParentExpanded.md)|Indica si se expandieron elementos primarios de la propiedad actual.|  
|[CMFCPropertyGridProperty::IsSelected](../Topic/CMFCPropertyGridProperty::IsSelected.md)|Indica si la propiedad actual está seleccionada.|  
|[CMFCPropertyGridProperty::IsVisible](../Topic/CMFCPropertyGridProperty::IsVisible.md)|Indica si la propiedad actual está visible.|  
|[CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)|Llamado por el marco cuando el usuario hace clic en un botón incluido en una propiedad.|  
|[CMFCPropertyGridProperty::OnClickName](../Topic/CMFCPropertyGridProperty::OnClickName.md)|Llamado por un control de lista de la propiedad parent cuando un usuario hace clic en el campo de nombre de una propiedad.|  
|[CMFCPropertyGridProperty::OnClickValue](../Topic/CMFCPropertyGridProperty::OnClickValue.md)|Llamado por un control de lista de la propiedad parent cuando un usuario hace clic en el campo Valor de una propiedad.|  
|[CMFCPropertyGridProperty::OnCloseCombo](../Topic/CMFCPropertyGridProperty::OnCloseCombo.md)|Llamado por el marco cuando se cierra un cuadro combinado de una propiedad.|  
|[CMFCPropertyGridProperty::OnDblClk](../Topic/CMFCPropertyGridProperty::OnDblClk.md)|Llamado por el marco cuando hace doble clic del usuario una propiedad.|  
|[CMFCPropertyGridProperty::OnDrawButton](../Topic/CMFCPropertyGridProperty::OnDrawButton.md)|Llamado por el marco para dibujar un botón de una propiedad.|  
|[CMFCPropertyGridProperty::OnDrawDescription](../Topic/CMFCPropertyGridProperty::OnDrawDescription.md)|Llamado por el marco para mostrar la descripción de la propiedad.|  
|[CMFCPropertyGridProperty::OnDrawExpandBox](../Topic/CMFCPropertyGridProperty::OnDrawExpandBox.md)|Llamado por el marco para dibujar un control de cuadro de expandir cerca de una propiedad que contiene sub\- propiedades.|  
|[CMFCPropertyGridProperty::OnDrawName](../Topic/CMFCPropertyGridProperty::OnDrawName.md)|Llamado por el marco para mostrar el nombre de propiedad.|  
|[CMFCPropertyGridProperty::OnDrawValue](../Topic/CMFCPropertyGridProperty::OnDrawValue.md)|Llamado por el marco para mostrar el valor de propiedad.|  
|[CMFCPropertyGridProperty::OnEdit](../Topic/CMFCPropertyGridProperty::OnEdit.md)|Llamado por el marco cuando el usuario está a punto de modificar un valor de propiedad.|  
|[CMFCPropertyGridProperty::OnEndEdit](../Topic/CMFCPropertyGridProperty::OnEndEdit.md)|Llamado por el marco cuando el usuario ha finalizado que modifica un valor de propiedad.|  
|[CMFCPropertyGridProperty::OnKillSelection](../Topic/CMFCPropertyGridProperty::OnKillSelection.md)||  
|[CMFCPropertyGridProperty::OnPosSizeChanged](../Topic/CMFCPropertyGridProperty::OnPosSizeChanged.md)||  
|[CMFCPropertyGridProperty::OnRClickName](../Topic/CMFCPropertyGridProperty::OnRClickName.md)|Llamado por el marco cuando el usuario hace clic con el botón secundario del mouse en el área de nombre de propiedad.|  
|[CMFCPropertyGridProperty::OnRClickValue](../Topic/CMFCPropertyGridProperty::OnRClickValue.md)|Llamado por el marco cuando el usuario hace clic con el botón secundario del mouse en el área de valores de propiedad.|  
|[CMFCPropertyGridProperty::OnSelectCombo](../Topic/CMFCPropertyGridProperty::OnSelectCombo.md)|Llamado por el marco cuando el usuario selecciona un elemento del cuadro combinado modificable.|  
|[CMFCPropertyGridProperty::OnSetCursor](../Topic/CMFCPropertyGridProperty::OnSetCursor.md)|Llamado por el marco cuando el puntero del mouse se mueve a un elemento de propiedad.|  
|[CMFCPropertyGridProperty::OnSetSelection](../Topic/CMFCPropertyGridProperty::OnSetSelection.md)||  
|[CMFCPropertyGridProperty::OnUpdateValue](../Topic/CMFCPropertyGridProperty::OnUpdateValue.md)|Llamado por el marco cuando el valor de una propiedad modificable ha cambiado.|  
|[CMFCPropertyGridProperty::PushChar](../Topic/CMFCPropertyGridProperty::PushChar.md)|Denominado de control de la lista de propiedades cuando la propiedad está seleccionado y el usuario escribe un nuevo carácter.|  
|[CMFCPropertyGridProperty::Redraw](../Topic/CMFCPropertyGridProperty::Redraw.md)|Redibuja la propiedad.|  
|[CMFCPropertyGridProperty::RemoveAllOptions](../Topic/CMFCPropertyGridProperty::RemoveAllOptions.md)|quita todas las opciones \(elementos\) de una propiedad.|  
|[CMFCPropertyGridProperty::RemoveSubItem](../Topic/CMFCPropertyGridProperty::RemoveSubItem.md)|quita el sub\-elemento especificado.|  
|[CMFCPropertyGridProperty::ResetOriginalValue](../Topic/CMFCPropertyGridProperty::ResetOriginalValue.md)|restablece el valor original de una propiedad editada.|  
|[CMFCPropertyGridProperty::SetData](../Topic/CMFCPropertyGridProperty::SetData.md)|Asocia un valor de `DWORD` a una propiedad.|  
|[CMFCPropertyGridProperty::SetDescription](../Topic/CMFCPropertyGridProperty::SetDescription.md)|especifica el texto que describe la propiedad actual.|  
|[CMFCPropertyGridProperty::SetName](../Topic/CMFCPropertyGridProperty::SetName.md)|Establece el nombre de una propiedad.|  
|[CMFCPropertyGridProperty::SetOriginalValue](../Topic/CMFCPropertyGridProperty::SetOriginalValue.md)|Establece el valor original de una propiedad modificable.|  
|[CMFCPropertyGridProperty::SetValue](../Topic/CMFCPropertyGridProperty::SetValue.md)|Establece el valor de una propiedad de la cuadrícula de propiedades.|  
|[CMFCPropertyGridProperty::Show](../Topic/CMFCPropertyGridProperty::Show.md)|Muestra u oculta una propiedad.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridProperty::CreateCombo](../Topic/CMFCPropertyGridProperty::CreateCombo.md)|Llamado por el marco para agregar un cuadro combinado en una propiedad.|  
|[CMFCPropertyGridProperty::HasButton](../Topic/CMFCPropertyGridProperty::HasButton.md)|indica si una propiedad contiene un botón.|  
|[CMFCPropertyGridProperty::Init](../Topic/CMFCPropertyGridProperty::Init.md)|Llamado por el marco para inicializar un objeto property.|  
|[CMFCPropertyGridProperty::IsSubItem](../Topic/CMFCPropertyGridProperty::IsSubItem.md)|Indica si la propiedad especificada es un sub\- elementos de propiedad actual.|  
|[CMFCPropertyGridProperty::IsValueChanged](../Topic/CMFCPropertyGridProperty::IsValueChanged.md)|indica si el valor de la propiedad actual ha cambiado.|  
|[CMFCPropertyGridProperty::OnCtlColor](../Topic/CMFCPropertyGridProperty::OnCtlColor.md)|Llamado por el marco cuando debe recuperar un pincel para rellenar el color de fondo de una propiedad.|  
|[CMFCPropertyGridProperty::OnDestroyWindow](../Topic/CMFCPropertyGridProperty::OnDestroyWindow.md)|Llamado por el marco cuando se destruye una propiedad o cuando edita finaliza.|  
|[CMFCPropertyGridProperty::OnKillFocus](../Topic/CMFCPropertyGridProperty::OnKillFocus.md)|Llamado por el marco cuando la propiedad pierde el foco de entrada.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridProperty::m\_strFormatDouble](../Topic/CMFCPropertyGridProperty::m_strFormatDouble.md)|Cadena de formato para un valor de tipo double.|  
|[CMFCPropertyGridProperty::m\_strFormatFloat](../Topic/CMFCPropertyGridProperty::m_strFormatFloat.md)|Cadena de formato para un valor de tipo float.|  
|[CMFCPropertyGridProperty::m\_strFormatLong](../Topic/CMFCPropertyGridProperty::m_strFormatLong.md)|Cadena de formato para un valor de tipo long.|  
|[CMFCPropertyGridProperty::m\_strFormatShort](../Topic/CMFCPropertyGridProperty::m_strFormatShort.md)|Cadena de formato para un valor de tipo short.|  
  
## Comentarios  
 Utilice un objeto de `CMFCPropertyGridProperty` para representar una propiedad, que posteriormente agrega un control de lista de propiedades.  Para obtener más información, vea [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
 Un objeto de propiedad puede representar tipos de datos como cadenas, fechas, y boolean o valores enteros.  Puede contener propiedades secundarias, o puede contener un control como un cuadro combinado o un control de botón.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCPropertyGridProperty` .  El ejemplo también muestra cómo utilizar varios métodos en la clase de `CMFCPropertyGridProperty` para agregar una opción, agregar un sub\- elemento, habilita una propiedad, y se muestra una propiedad.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#27](../../mfc/reference/codesnippet/CPP/cmfcpropertygridproperty-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
## Requisitos  
 **encabezado:** afxpropertygridctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)