---
title: "CButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "button control [MFC]"
  - "button objects (CButton)"
  - "CButton class"
  - "casillas, button controls"
  - "checkbox buttons"
  - "pushbuttons"
  - "botones de opción, CButton class"
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de los controles de botón de Windows.  
  
## Sintaxis  
  
```  
class CButton : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CButton::CButton](../Topic/CButton::CButton.md)|Crea un objeto `CButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CButton::Create](../Topic/CButton::Create.md)|Hace que el control de botón de Windows y lo asocia al objeto de `CButton` .|  
|[CButton::DrawItem](../Topic/CButton::DrawItem.md)|Reemplazo para dibujar un objeto dibujado por de `CButton` .|  
|[CButton::GetBitmap](../Topic/CButton::GetBitmap.md)|Recupera el identificador del mapa de bits establecido previamente con [SetBitmap](../Topic/CButton::SetBitmap.md).|  
|[CButton::GetButtonStyle](../Topic/CButton::GetButtonStyle.md)|Recupera información sobre el estilo del control de botón.|  
|[CButton::GetCheck](../Topic/CButton::GetCheck.md)|Recupera el estado de la comprobación de un control de botón.|  
|[CButton::GetCursor](../Topic/CButton::GetCursor.md)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](../Topic/CButton::SetCursor.md).|  
|[CButton::GetIcon](../Topic/CButton::GetIcon.md)|Recupera el identificador del icono establecido previamente con [SetIcon](../Topic/CButton::SetIcon.md).|  
|[CButton::GetIdealSize](../Topic/CButton::GetIdealSize.md)|Recupera el tamaño ideal de control button.|  
|[CButton::GetImageList](../Topic/CButton::GetImageList.md)|Recupera la lista del control de botón.|  
|[CButton::GetNote](../Topic/CButton::GetNote.md)|Recupera el componente de la nota de control de vínculo de comando actual.|  
|[CButton::GetNoteLength](../Topic/CButton::GetNoteLength.md)|Recupera la longitud del texto de la nota para el control de vínculo de comando actual.|  
|[CButton::GetSplitGlyph](../Topic/CButton::GetSplitGlyph.md)|Recupera el glifo asociado al control actual de botón de expansión.|  
|[CButton::GetSplitImageList](../Topic/CButton::GetSplitImageList.md)|Recupera la lista de imágenes del control actual de botón de expansión.|  
|[CButton::GetSplitInfo](../Topic/CButton::GetSplitInfo.md)|Recupera información que define el control actual de botón de expansión.|  
|[CButton::GetSplitSize](../Topic/CButton::GetSplitSize.md)|Recupera el rectángulo delimitador del componente desplegable del control actual de botón de expansión.|  
|[CButton::GetSplitStyle](../Topic/CButton::GetSplitStyle.md)|Recupera los estilos de botón de expansión que definen el control actual de botón de expansión.|  
|[CButton::GetState](../Topic/CButton::GetState.md)|Recupera el estado de activación, el estado de resaltado, y el estado del foco de un control de botón.|  
|[CButton::GetTextMargin](../Topic/CButton::GetTextMargin.md)|Recupera el marcado del texto del control de botón.|  
|[CButton::SetBitmap](../Topic/CButton::SetBitmap.md)|especifica un mapa de bits que se mostrará en el botón.|  
|[CButton::SetButtonStyle](../Topic/CButton::SetButtonStyle.md)|cambia el estilo de un botón.|  
|[CButton::SetCheck](../Topic/CButton::SetCheck.md)|Establece el estado de la comprobación de un control de botón.|  
|[CButton::SetCursor](../Topic/CButton::SetCursor.md)|Especifica una imagen de cursor que se va a mostrar en el botón.|  
|[CButton::SetDropDownState](../Topic/CButton::SetDropDownState.md)|Establece el estado desplegable del control actual de botón de expansión.|  
|[CButton::SetIcon](../Topic/CButton::SetIcon.md)|especifica un icono que se mostrará en el botón.|  
|[CButton::SetImageList](../Topic/CButton::SetImageList.md)|Establece la lista del control de botón.|  
|[CButton::SetNote](../Topic/CButton::SetNote.md)|Establece la nota en el control de vínculo de comando actual.|  
|[CButton::SetSplitGlyph](../Topic/CButton::SetSplitGlyph.md)|Asocia un glifo especificado al control actual de botón de expansión.|  
|[CButton::SetSplitImageList](../Topic/CButton::SetSplitImageList.md)|Asocia una lista de imágenes al control actual de botón de expansión.|  
|[CButton::SetSplitInfo](../Topic/CButton::SetSplitInfo.md)|Especifica información que define el control actual de botón de expansión.|  
|[CButton::SetSplitSize](../Topic/CButton::SetSplitSize.md)|Establece el rectángulo delimitador del componente desplegable del control actual de botón de expansión.|  
|[CButton::SetSplitStyle](../Topic/CButton::SetSplitStyle.md)|Establece el estilo del control actual de botón de expansión.|  
|[CButton::SetState](../Topic/CButton::SetState.md)|Establece el estado del resaltado de un control de botón.|  
|[CButton::SetTextMargin](../Topic/CButton::SetTextMargin.md)|Establece el marcado del texto del control de botón.|  
  
## Comentarios  
 un control de botón es una ventana secundaria pequeña, rectangular que se puede hacer clic por intervalos.  Los botones sólo se pueden utilizar o en grupos y pueden ser etiquetados o aparecen sin texto.  Un botón cambia normalmente aspecto cuando el usuario hace clic en.  
  
 Los botones normales son la casilla, el botón de radio, y el mismo botón.  Un objeto de `CButton` puede ser cualquiera de estos, como [estilo de botón](../../mfc/reference/button-styles.md) especificado en su inicialización por la función miembro de [Crear](../Topic/CButton::Create.md) .  
  
 Además, la clase de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) derivada de `CButton` admite la creación de los controles de botón etiquetados con imágenes de mapa de bits en lugar de texto.  `CBitmapButton` puede tener mapas de bits independientes para un botón hacia arriba, abajo, que tiene el foco, y estados disabled.  
  
 Puede crear un control de botón de una plantilla de cuadro de diálogo o directamente en el código.  En ambos casos, llame primero al constructor `CButton` para construir el objeto de `CButton` ; llamar a continuación a la función miembro de **Crear** para crear el control de botón de Windows y para adjuntarlo al objeto de `CButton` .  
  
 la construcción puede ser un proceso de un solo paso en una clase derivada de `CButton`.  Escriba un constructor para la clase derivada y llame a **Crear** dentro del constructor.  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un control button a su elemento primario \(normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)\), agregue una función miembro de entrada y controlador de mensajes de mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 notificación**\(**`id`, `memberFxn`**\)**de**ON\_**  
  
 donde `id` especifica el identificador de ventana secundaria de control que envía la notificación y `memberFxn` es el nombre de la función principal del miembro que ha escrito para controlar la notificación.  
  
 El prototipo de función del elemento primario es el siguiente:  
  
 **afx\_msg** `void` `memberFxn`\(\);  
  
 Las entradas posibles de mapa de mensajes son los siguientes:  
  
|Entrada de asignación|Enviado al elemento primario cuando…|  
|---------------------------|------------------------------------------|  
|**TODOS**|El usuario hace clic en un botón.|  
|**ON\_BN\_DOUBLECLICKED**|El usuario hace doble clic en un botón.|  
  
 Si crea un objeto de `CButton` de un recurso de cuadro de diálogo, el objeto de `CButton` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CButton` dentro de una ventana, puede necesitar destruirla.  Si crea el objeto de `CButton` en la pila mediante la función de **nuevo** , debe llamar a **cancelación** en el objeto para destruirlo cuando el usuario cierra el control de botón de Windows.  Si crea el objeto de `CButton` en la pila, o se inserta en el objeto primario del cuadro de diálogo, se destruye automáticamente.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton Class](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)