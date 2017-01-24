---
title: "CRichEditCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl class"
  - "CRichEditCtrl class, controles comunes"
  - "formatted text [C++]"
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control rich edit.  
  
## Sintaxis  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](../Topic/CRichEditCtrl::CRichEditCtrl.md)|Crea un objeto `CRichEditCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](../Topic/CRichEditCtrl::CanPaste.md)|Determina si el contenido del portapapeles se puede pegar en este control rich edit.|  
|[CRichEditCtrl::CanRedo](../Topic/CRichEditCtrl::CanRedo.md)|Determina si hay acciones en la cola de rehacer del control.|  
|[CRichEditCtrl::CanUndo](../Topic/CRichEditCtrl::CanUndo.md)|Determina si una operación de edición se puede deshacer.|  
|[CRichEditCtrl::CharFromPos](../Topic/CRichEditCtrl::CharFromPos.md)|Recupera información sobre el carácter más próximo a un punto especificado en el área cliente de un control de edición.|  
|[CRichEditCtrl::Clear](../Topic/CRichEditCtrl::Clear.md)|Borra la selección actual.|  
|[CRichEditCtrl::Copy](../Topic/CRichEditCtrl::Copy.md)|Copia la selección actual en el portapapeles.|  
|[CRichEditCtrl::Create](../Topic/CRichEditCtrl::Create.md)|Crea el control rich edit de Windows y lo asocia a este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::CreateEx](../Topic/CRichEditCtrl::CreateEx.md)|Crea el control rich edit de Windows con estilos extendidos especificados de Windows y lo asocia a este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::Cut](../Topic/CRichEditCtrl::Cut.md)|Corta la selección actual en el portapapeles.|  
|[CRichEditCtrl::DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md)|Muestra una parte del contenido de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::EmptyUndoBuffer](../Topic/CRichEditCtrl::EmptyUndoBuffer.md)|Restaura \(claro\) el indicador de deshacer de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::FindText](../Topic/CRichEditCtrl::FindText.md)|Busque el texto dentro de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::FindWordBreak](../Topic/CRichEditCtrl::FindWordBreak.md)|Encuentra la interrupción siguiente de la palabra antes o después de la posición de caracteres especificada, o recuperar información sobre el carácter en esa posición.|  
|[CRichEditCtrl::FormatRange](../Topic/CRichEditCtrl::FormatRange.md)|Da formato a un intervalo de texto para el dispositivo de salida de destino.|  
|[CRichEditCtrl::GetCharPos](../Topic/CRichEditCtrl::GetCharPos.md)|Determina la ubicación de un carácter específico en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md)|Recupera atributos predeterminados actuales del formato de caracteres en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md)|Recupera la máscara de evento para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetFirstVisibleLine](../Topic/CRichEditCtrl::GetFirstVisibleLine.md)|Determina la línea visible superior en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetIRichEditOle](../Topic/CRichEditCtrl::GetIRichEditOle.md)|Recupera un puntero a la interfaz de `IRichEditOle` para este control rich edit.|  
|[CRichEditCtrl::GetLimitText](../Topic/CRichEditCtrl::GetLimitText.md)|Obtiene el límite en la cantidad de texto que un usuario escriba en este `CRichEditCtrl` el objeto.|  
|[CRichEditCtrl::GetLine](../Topic/CRichEditCtrl::GetLine.md)|recupera una línea de texto de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetLineCount](../Topic/CRichEditCtrl::GetLineCount.md)|Recupera el número de líneas de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetModify](../Topic/CRichEditCtrl::GetModify.md)|Determina si el contenido de este objeto de `CRichEditCtrl` han cambiado desde la última vez.|  
|[CRichEditCtrl::GetOptions](../Topic/CRichEditCtrl::GetOptions.md)|Recupera las opciones avanzadas del control de edición.|  
|[CRichEditCtrl::GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md)|Recupera los atributos de formato de párrafo en la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetPunctuation](../Topic/CRichEditCtrl::GetPunctuation.md)|Recupera los caracteres de puntuación actuales del control rich edit.  Este mensaje solo está disponible en las versiones lingüísticas del sistema operativo.|  
|[CRichEditCtrl::GetRect](../Topic/CRichEditCtrl::GetRect.md)|Recupera el rectángulo de formato para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetRedoName](../Topic/CRichEditCtrl::GetRedoName.md)|Recupera el tipo de acción siguiente, si existe, en la cola de rehacer del control.|  
|[CRichEditCtrl::GetSel](../Topic/CRichEditCtrl::GetSel.md)|Obtiene las posiciones de inicio y fin de la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md)|Recupera los atributos de formato de caracteres de la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md)|Recupera el tipo de contenido en la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::GetSelText](../Topic/CRichEditCtrl::GetSelText.md)|Obtiene el texto de la selección actual de este objeto de `CRichEditCtrl`|  
|[CRichEditCtrl::GetTextLength](../Topic/CRichEditCtrl::GetTextLength.md)|Recupera la longitud del texto, en caracteres, de este objeto de `CRichEditCtrl` .  No incluye el carácter null de terminación.|  
|[CRichEditCtrl::GetTextLengthEx](../Topic/CRichEditCtrl::GetTextLengthEx.md)|Recupera el número de caracteres o bytes en la vista completa de la edición.  Acepta una lista de marcas para indicar el método para determinar la longitud del texto en un control rich edit|  
|[CRichEditCtrl::GetTextMode](../Topic/CRichEditCtrl::GetTextMode.md)|Recupera el modo de texto y deshacer actuales de nivel de un control rich edit.|  
|[CRichEditCtrl::GetTextRange](../Topic/CRichEditCtrl::GetTextRange.md)|Recupera el intervalo de texto especificado.|  
|[CRichEditCtrl::GetUndoName](../Topic/CRichEditCtrl::GetUndoName.md)|Recupera el tipo de la siguiente acción de deshacer, si existe.|  
|[CRichEditCtrl::GetWordWrapMode](../Topic/CRichEditCtrl::GetWordWrapMode.md)|Recupera las opciones actuales del ajuste de línea y de separación de palabras para el control rich edit.  Este mensaje solo está disponible en las versiones lingüísticas del sistema operativo.|  
|[CRichEditCtrl::HideSelection](../Topic/CRichEditCtrl::HideSelection.md)|Muestra u oculta la selección actual.|  
|[CRichEditCtrl::LimitText](../Topic/CRichEditCtrl::LimitText.md)|Limita la cantidad de texto que un usuario puede escribir en `CRichEditCtrl` el objeto.|  
|[CRichEditCtrl::LineFromChar](../Topic/CRichEditCtrl::LineFromChar.md)|Determina que la línea contiene el carácter dado.|  
|[CRichEditCtrl::LineIndex](../Topic/CRichEditCtrl::LineIndex.md)|Recupera el índice del carácter de una línea determinada de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::LineLength](../Topic/CRichEditCtrl::LineLength.md)|Recupera la longitud de una línea determinada de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::LineScroll](../Topic/CRichEditCtrl::LineScroll.md)|Desplaza el texto en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::Paste](../Topic/CRichEditCtrl::Paste.md)|Inserta el contenido del portapapeles en este control rich edit.|  
|[CRichEditCtrl::PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md)|Inserta el contenido del portapapeles en este control rich edit en el formato de datos especificado.|  
|[CRichEditCtrl::PosFromChar](../Topic/CRichEditCtrl::PosFromChar.md)|Recupera las coordenadas del área cliente de un carácter especificado en un control de edición.|  
|[CRichEditCtrl::Redo](../Topic/CRichEditCtrl::Redo.md)|Rehace la siguiente acción de la cola rehacer del control.|  
|[CRichEditCtrl::ReplaceSel](../Topic/CRichEditCtrl::ReplaceSel.md)|Reemplaza la selección actual de este objeto de `CRichEditCtrl` con el texto especificado.|  
|[CRichEditCtrl::RequestResize](../Topic/CRichEditCtrl::RequestResize.md)|Convierte este objeto de `CRichEditCtrl` para enviar solicitud cambian el tamaño notificaciones.|  
|[CRichEditCtrl::SetAutoURLDetect](../Topic/CRichEditCtrl::SetAutoURLDetect.md)|Indica si la detección automática de la dirección URL está activo en un control rich edit.|  
|[CRichEditCtrl::SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md)|Establece el color de fondo en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md)|Establece los atributos predeterminados actuales del formato de caracteres en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md)|Establece la máscara de evento para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetModify](../Topic/CRichEditCtrl::SetModify.md)|Obtiene o borrar la marca de modificación para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetOLECallback](../Topic/CRichEditCtrl::SetOLECallback.md)|Establece el objeto COM de `IRichEditOleCallback` para este control rich edit.|  
|[CRichEditCtrl::SetOptions](../Topic/CRichEditCtrl::SetOptions.md)|establece las opciones para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md)|Establece los atributos de formato de párrafo en la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetPunctuation](../Topic/CRichEditCtrl::SetPunctuation.md)|Establece los caracteres de puntuación para un control rich edit.  Este mensaje solo está disponible en las versiones lingüísticas del sistema operativo.|  
|[CRichEditCtrl::SetReadOnly](../Topic/CRichEditCtrl::SetReadOnly.md)|Establece la opción de solo lectura para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetRect](../Topic/CRichEditCtrl::SetRect.md)|Establece el rectángulo de formato para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetSel](../Topic/CRichEditCtrl::SetSel.md)|Establece la selección en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md)|Establece los atributos de formato de caracteres de la selección actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md)|Establece el dispositivo de salida de destino para este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetTextMode](../Topic/CRichEditCtrl::SetTextMode.md)|Establece el modo de texto o deshacer level de un control rich edit.  El mensaje no se supera si el control contiene el texto.|  
|[CRichEditCtrl::SetUndoLimit](../Topic/CRichEditCtrl::SetUndoLimit.md)|Establece el número máximo de acciones que pueden almacenarse en la cola de deshacer.|  
|[CRichEditCtrl::SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md)|Establece los atributos de formato de caracteres de la palabra actual de este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::SetWordWrapMode](../Topic/CRichEditCtrl::SetWordWrapMode.md)|Establece el ajuste automático de líneas y opciones de separación de palabras para el control rich edit.  Este mensaje solo está disponible en las versiones lingüísticas del sistema operativo.|  
|[CRichEditCtrl::StopGroupTyping](../Topic/CRichEditCtrl::StopGroupTyping.md)|Detiene el control de obtener acciones que escriben adicionales en la acción actual de deshacer.  El control almacena la acción que escribe siguiente, si existe, en una nueva acción en la cola de deshacer.|  
|[CRichEditCtrl::StreamIn](../Topic/CRichEditCtrl::StreamIn.md)|Las insertar texto de un flujo de entrada en este objeto de `CRichEditCtrl` .|  
|[CRichEditCtrl::StreamOut](../Topic/CRichEditCtrl::StreamOut.md)|Los almacenes texto de este objeto de `CRichEditCtrl` en un flujo de salida.|  
|[CRichEditCtrl::Undo](../Topic/CRichEditCtrl::Undo.md)|Invierte la última operación de edición.|  
  
## Comentarios  
 Un “control rich edit” es una ventana en la que el usuario puede escribir y modificar texto.  el texto se puede asignar el carácter y el formato de párrafo, y puede incluir objetos OLE incrustados.  Los controles rich edit proporcionan una interfaz de programación para dar formato al texto.  Sin embargo, una aplicación debe implementar cualquier componente de la interfaz de usuario necesario colocar operaciones de formato a disposición del usuario.  
  
 Este control común de Windows \(y por consiguiente la clase de `CRichEditCtrl` \) sólo está disponible para los programas que se ejecutan en versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  La clase de `CRichEditCtrl` admite las versiones 2,0 y 3,0 del control de edición amplio de [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] .  
  
> [!CAUTION]
>  Si utiliza un control rich edit en un cuadro de diálogo \(independientemente de si la aplicación es SDI, MDI, o diálogo\- basado\), debe llamar a [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) una vez antes de que se muestre el cuadro de diálogo.  Un lugar típico para llamar a esta función es la función miembro de `InitInstance` del programa.  No necesita llamarlo para cada vez que se muestra el cuadro de diálogo, solo la primera vez.  No tiene que llamar a `AfxInitRichEdit` si trabaja con `CRichEditView`.  
  
 Para obtener más información sobre cómo utilizar `CRichEditCtrl`, vea:  
  
-   [Controles](../../mfc/controls-mfc.md)  
  
-   [Mediante CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   Caso Q259949 de Knowledge Base: INFO: SetCaretPos\(\) no Adecuado con CEdit o Controles de CRichEditCtrl  
  
 Para obtener un ejemplo de cómo utilizar un control rich edit en una aplicación MFC, vea la aplicación de ejemplo de [WORDPAD](../../top/visual-cpp-samples.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo WORDPAD de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)