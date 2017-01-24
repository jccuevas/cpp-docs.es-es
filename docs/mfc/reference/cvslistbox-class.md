---
title: "CVSListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CVSListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVSListBox class"
  - "CVSListBox::PreTranslateMessage method"
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
caps.latest.revision: 30
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CVSListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CVSListBox` admite un control de lista modificable.  
  
## Sintaxis  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](../Topic/CVSListBox::CVSListBox.md)|Crea un objeto `CVSListBox`.|  
|`CVSListBox::~CVSListBox`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CVSListBox::AddItem](../Topic/CVSListBox::AddItem.md)|agrega una cadena a un control de lista.  \(Reemplaza `CVSListBoxBase::AddItem`.\)|  
|[CVSListBox::EditItem](../Topic/CVSListBox::EditItem.md)|Comienza una operación de edición de texto de un elemento de control list.  \(Reemplaza `CVSListBoxBase::EditItem`.\)|  
|[CVSListBox::GetCount](../Topic/CVSListBox::GetCount.md)|Recupera el número de cadenas en un control de lista modificable.  \(Reemplaza `CVSListBoxBase::GetCount`.\)|  
|[CVSListBox::GetItemData](../Topic/CVSListBox::GetItemData.md)|Recupera un valor de 32 bits específico de la aplicación que está asociado a un elemento modificable del control de lista.  \(Reemplaza `CVSListBoxBase::GetItemData`.\)|  
|[CVSListBox::GetItemText](../Topic/CVSListBox::GetItemText.md)|Recupera el texto de un elemento modificable del control de lista.  \(Reemplaza `CVSListBoxBase::GetItemText`.\)|  
|[CVSListBox::GetSelItem](../Topic/CVSListBox::GetSelItem.md)|Recupera el índice de base cero del elemento actualmente seleccionado en un control de lista modificable.  \(Reemplaza `CVSListBoxBase::GetSelItem`.\)|  
|`CVSListBox::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  Para obtener más sintaxis de información y de método, vea [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).  \(Reemplaza `CVSListBoxBase::PreTranslateMessage`.\)|  
|[CVSListBox::RemoveItem](../Topic/CVSListBox::RemoveItem.md)|Quita un elemento de un control de lista modificable.  \(Reemplaza `CVSListBoxBase::RemoveItem`.\)|  
|[CVSListBox::SelectItem](../Topic/CVSListBox::SelectItem.md)|Selecciona una cadena modificable del control de lista.  \(Reemplaza `CVSListBoxBase::SelectItem`.\)|  
|[CVSListBox::SetItemData](../Topic/CVSListBox::SetItemData.md)|Asocia un valor de 32 bits específico de la aplicación a un elemento modificable del control de lista.  \(Reemplaza `CVSListBoxBase::SetItemData`.\)|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](../Topic/CVSListBox::GetListHwnd.md)|Devuelve el identificador al control incrustado actual de la vista de lista.|  
  
## Comentarios  
 La clase de `CVSListBox` proporciona un conjunto de botones de edición que permiten al usuario para crear, modificar, eliminar, o para reorganizar los elementos en un control de lista.  
  
 A continuación se muestra una imagen del control de lista modificable.  La segunda entrada de lista, que se denomina “Elemento2”, está seleccionado para editar.  
  
 ![Control CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Si utiliza el editor de recursos para agregar un control editable de la lista, observe que el panel de **Cuadro de herramientas** del editor no proporciona un control modificable predefinido de la lista.  En su lugar, agregue un control estático como el control de **Cuadro de grupo** .  El marco de trabajo usa el control estático como marcador para especificar el tamaño y la posición del control de lista modificable.  
  
 Para utilizar un control de lista modificable en una plantilla de cuadro de diálogo, declare una variable de `CVSListBox` en la del cuadro de diálogo.  Para admitir el intercambio de datos entre la variable y el control, defina una entrada de macro de `DDX_Control` en el método de `DoDataExchange` del cuadro de diálogo.  De forma predeterminada, el control de lista modificable se crea sin los botones de edición.  Utilice el método heredado de [CVSListBoxBase::SetStandardButtons](http://msdn.microsoft.com/es-es/129e530f-97e9-42eb-b128-371c2a5686ba) para habilitar los botones de edición.  
  
 Para obtener más información, vea el directorio de ejemplos, el ejemplo de `New Controls` , los archivos de Page3.cpp y de Page3.h.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## Requisitos  
 **encabezado:** afxvslistbox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)