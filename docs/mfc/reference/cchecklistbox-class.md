---
title: "CCheckListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCheckListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCheckListBox class"
  - "checklist boxes"
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CCheckListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de un cuadro de lista de comprobación de Windows.  
  
## Sintaxis  
  
```  
  
class CCheckListBox : public CListBox  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](../Topic/CCheckListBox::CCheckListBox.md)|Crea un objeto `CCheckListBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCheckListBox::Create](../Topic/CCheckListBox::Create.md)|Crea el cuadro de lista de comprobación de Windows y lo asocia al objeto de `CCheckListBox` .|  
|[CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md)|Llamado por el marco cuando un aspecto visual de los cambios de un cuadro de lista de dibujo propietario.|  
|[CCheckListBox::Enable](../Topic/CCheckListBox::Enable.md)|Permisos o neutralizaciones un elemento del cuadro de lista de comprobación.|  
|[CCheckListBox::GetCheck](../Topic/CCheckListBox::GetCheck.md)|Obtiene el estado de la casilla de un elemento.|  
|[CCheckListBox::GetCheckStyle](../Topic/CCheckListBox::GetCheckStyle.md)|Obtiene el estilo de las casillas del control.|  
|[CCheckListBox::IsEnabled](../Topic/CCheckListBox::IsEnabled.md)|Determina si un elemento está habilitado.|  
|[CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md)|Llamado por el marco cuando un cuadro de lista con un estilo de dibujo propietario se crea.|  
|[CCheckListBox::OnGetCheckPosition](../Topic/CCheckListBox::OnGetCheckPosition.md)|Llamado por el marco para obtener la posición de la casilla de un elemento.|  
|[CCheckListBox::SetCheck](../Topic/CCheckListBox::SetCheck.md)|Establece el estado de la casilla de un elemento.|  
|[CCheckListBox::SetCheckStyle](../Topic/CCheckListBox::SetCheckStyle.md)|Establece el estilo de las casillas del control.|  
  
## Comentarios  
 Un “cuadro de lista de comprobación” muestra una lista de elementos, como nombres de archivo.  Cada elemento de la lista tiene una casilla junto al que el usuario puede comprobar o borrar.  
  
 `CCheckListBox` sólo para los controles propietario\- dibujados porque la lista contiene más que las cadenas de texto.  En su versión más simple, un cuadro de lista de comprobación contiene las cadenas de texto y las casillas, pero no necesita tener texto en absoluto.  Por ejemplo, podría tener una lista de pequeños mapas de bits con una casilla junto a cada elemento.  
  
 Para crear su propio cuadro de lista de comprobación, debe derivar su propia clase de `CCheckListBox`.  Para derivar su propia clase, escriba un constructor para la clase derivada, llame a **Create**.  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista al elemento primario \(normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)\), agregue una función miembro de entrada y controlador de mensajes de mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 notificación**\(**`id`, `memberFxn`**\)**de**ON\_**  
  
 donde `id` especifica el identificador de ventana secundaria de control que envía la notificación y `memberFxn` es el nombre de la función principal del miembro que ha escrito para controlar la notificación.  
  
 El prototipo de función del elemento primario es el siguiente:  
  
 **afx\_msg** `void` `memberFxn`\(\);  
  
 Sólo hay una entrada de mensaje\- mapa correspondiente específicamente a **CCheckListBox** \(pero vea también las entradas de mensaje\- mapa para [CListBox](../../mfc/reference/clistbox-class.md)\):  
  
-   El usuario de**ON\_CLBN\_CHKCHANGE** The ha cambiado el estado de la casilla de un elemento.  
  
 Si el cuadro de lista de comprobación es cuadro predeterminado de la lista de comprobación \(una lista de cadenas con las casillas valor por defecto\- ordenadas a la izquierda de cada\), puede utilizar el valor predeterminado [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) para dibujar el cuadro de lista de comprobación.  Si no, debe reemplazar la función de [CListBox::CompareItem](../Topic/CListBox::CompareItem.md) y [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) y [CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md) funciona.  
  
 Puede crear un cuadro de lista de comprobación de una plantilla de cuadro de diálogo o directamente en el código.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo TSTCON de MFC](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)