---
title: "CEdit Class | Microsoft Docs"
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
  - "CEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEdit class"
  - "controles [MFC], edit"
  - "edit controls"
  - "edit controls, clases"
  - "line separators in multiline edit controls"
  - "multiline edit control"
  - "separadores, in multiline edit controls"
  - "text editors"
  - "text editors, CEdit class"
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
caps.latest.revision: 22
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de un control de edición de Windows.  
  
## Sintaxis  
  
```  
class CEdit : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEdit::CEdit](../Topic/CEdit::CEdit.md)|Construye un objeto de control de `CEdit` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEdit::CanUndo](../Topic/CEdit::CanUndo.md)|Determina si una operación de control de edición se puede deshacer.|  
|[CEdit::CharFromPos](../Topic/CEdit::CharFromPos.md)|Recupera los índices de la línea y de carácter a carácter más próximo a una posición especificada.|  
|[CEdit::Clear](../Topic/CEdit::Clear.md)|Elimina \(desactivada\) la selección actual \(si existe\) al control de edición.|  
|[CEdit::Copy](../Topic/CEdit::Copy.md)|Copia la selección actual \(si existe\) al control de edición al portapapeles en el formato de **CF\_TEXT** .|  
|[CEdit::Create](../Topic/CEdit::Create.md)|Hace que el control de edición de Windows y lo asocia al objeto de `CEdit` .|  
|[CEdit::Cut](../Topic/CEdit::Cut.md)|Elimina \(cortes\) la selección actual \(si existe\) al control de edición y copia el texto eliminado en el portapapeles en el formato de **CF\_TEXT** .|  
|[CEdit::EmptyUndoBuffer](../Topic/CEdit::EmptyUndoBuffer.md)|Restaura \(desactivada\) el indicador de deshacer de un control de edición.|  
|[CEdit::FmtLines](../Topic/CEdit::FmtLines.md)|Establece la inclusión de los caracteres de salto de línea suaves con. o dentro de un control de edición de varias líneas.|  
|[CEdit::GetCueBanner](../Topic/CEdit::GetCueBanner.md)|Recupera el texto que se muestra como la señal de texto, o sugerencias, en un control de edición cuando el control está vacío y no tiene el foco.|  
|[CEdit::GetFirstVisibleLine](../Topic/CEdit::GetFirstVisibleLine.md)|determina la línea visible superior en un control de edición.|  
|[CEdit::GetHandle](../Topic/CEdit::GetHandle.md)|Recupera un identificador de memoria asignado actualmente para un control de edición de varias líneas.|  
|[CEdit::GetHighlight](../Topic/CEdit::GetHighlight.md)|Obtiene los índices de los caracteres inicial y final de un intervalo de texto que se muestra resaltado en el control de edición actual.|  
|[CEdit::GetLimitText](../Topic/CEdit::GetLimitText.md)|Obtiene la cantidad máxima de texto que este `CEdit` puede contener.|  
|[CEdit::GetLine](../Topic/CEdit::GetLine.md)|recupera una línea de texto de un control de edición.|  
|[CEdit::GetLineCount](../Topic/CEdit::GetLineCount.md)|recupera el número de líneas en un control de edición de varias líneas.|  
|[CEdit::GetMargins](../Topic/CEdit::GetMargins.md)|Obtiene los márgenes izquierdo y derecho para este `CEdit`.|  
|[CEdit::GetModify](../Topic/CEdit::GetModify.md)|Determina si el contenido de un control de edición se han modificado.|  
|[CEdit::GetPasswordChar](../Topic/CEdit::GetPasswordChar.md)|Recupera el carácter de contraseña mostrado en un control de edición cuando el usuario escribe texto.|  
|[CEdit::GetRect](../Topic/CEdit::GetRect.md)|Obtiene el rectángulo de formato de un control de edición.|  
|[CEdit::GetSel](../Topic/CEdit::GetSel.md)|Obtiene la primera y la última posición de caracteres de la selección actual en un control de edición.|  
|[CEdit::HideBalloonTip](../Topic/CEdit::HideBalloonTip.md)|Oculta el globo de sugerencias asociado al control de edición actual.|  
|[CEdit::LimitText](../Topic/CEdit::LimitText.md)|Restringe la longitud de texto que el usuario escriba en un control de edición.|  
|[CEdit::LineFromChar](../Topic/CEdit::LineFromChar.md)|Recupera el número de línea que contiene el índice de caracteres especificado.|  
|[CEdit::LineIndex](../Topic/CEdit::LineIndex.md)|Recupera el índice del carácter de una línea dentro de un control de edición de varias líneas.|  
|[CEdit::LineLength](../Topic/CEdit::LineLength.md)|recupera la longitud de una línea en un control de edición.|  
|[CEdit::LineScroll](../Topic/CEdit::LineScroll.md)|desplaza el texto de un control de edición de varias líneas.|  
|[CEdit::Paste](../Topic/CEdit::Paste.md)|Inserta los datos del portapapeles en el control de edición en la posición del cursor actual.  Se inserta los datos sólo si el portapapeles contiene datos en el formato de **CF\_TEXT** .|  
|[CEdit::PosFromChar](../Topic/CEdit::PosFromChar.md)|Recupera las coordenadas de la esquina superior izquierda de un índice de caracteres especificado.|  
|[CEdit::ReplaceSel](../Topic/CEdit::ReplaceSel.md)|reemplaza la selección actual en un control de edición con el texto especificado.|  
|[CEdit::SetCueBanner](../Topic/CEdit::SetCueBanner.md)|Establece el texto que se mostrará como la señal de texto, o sugerencias, en un control de edición cuando el control está vacío y no tiene el foco.|  
|[CEdit::SetHandle](../Topic/CEdit::SetHandle.md)|Establece el identificador a la memoria local que se utiliza en un control de edición de varias líneas.|  
|[CEdit::SetHighlight](../Topic/CEdit::SetHighlight.md)|Resalta un intervalo de texto que se muestra en el control de edición actual.|  
|[CEdit::SetLimitText](../Topic/CEdit::SetLimitText.md)|Establece la cantidad máxima de texto que este `CEdit` puede contener.|  
|[CEdit::SetMargins](../Topic/CEdit::SetMargins.md)|Establece los márgenes izquierdo y derecho para este `CEdit`.|  
|[CEdit::SetModify](../Topic/CEdit::SetModify.md)|Establece o desactive el indicador de modificación para un control de edición.|  
|[CEdit::SetPasswordChar](../Topic/CEdit::SetPasswordChar.md)|Establece o quita un carácter de contraseña mostrado en un control de edición cuando el usuario escribe texto.|  
|[CEdit::SetReadOnly](../Topic/CEdit::SetReadOnly.md)|Establece el estado de sólo lectura de un control de edición.|  
|[CEdit::SetRect](../Topic/CEdit::SetRect.md)|Establece el rectángulo de formato de un control de edición de varias líneas y actualiza el control.|  
|[CEdit::SetRectNP](../Topic/CEdit::SetRectNP.md)|Establece el rectángulo de formato de un control de edición de varias líneas sin optimizar la ventana de control.|  
|[CEdit::SetSel](../Topic/CEdit::SetSel.md)|Seleccione un intervalo de caracteres en un control de edición.|  
|[CEdit::SetTabStops](../Topic/CEdit::SetTabStops.md)|Establecen tabulaciones en un control de edición de varias líneas.|  
|[CEdit::ShowBalloonTip](../Topic/CEdit::ShowBalloonTip.md)|Muestra un globo de sugerencias que está asociado al control de edición actual.|  
|[CEdit::Undo](../Topic/CEdit::Undo.md)|Anula la operación de control de última edición.|  
  
## Comentarios  
 Un control de edición es una ventana secundaria rectangular en la que el usuario puede escribir texto.  
  
 Puede crear un control de edición de una plantilla de cuadro de diálogo o directamente en el código.  En ambos casos, llame primero al constructor `CEdit` para construir el objeto de `CEdit` , después llamar a la función miembro de [Crear](../Topic/CEdit::Create.md) para crear el control de edición y adjuntar de Windows en el objeto de `CEdit` .  
  
 la construcción puede ser un proceso de un solo paso en una clase derivada de `CEdit`.  Escriba un constructor para la clase derivada y llame a **Crear** dentro del constructor.  
  
 `CEdit` hereda la funcionalidad significativa de `CWnd`.  Para establecer y recuperar texto de un objeto de `CEdit` , utilice las funciones [SetWindowText](../Topic/CWnd::SetWindowText.md) y [GetWindowText](../Topic/CWnd::GetWindowText.md)miembro de `CWnd` , que establecen u obtiene todo el contenido de un control de edición, aunque es un control de varias líneas.  Las líneas de texto en un control de múltiples líneas están separadas por “\\ secuencias de caracteres de r \\ n”.  Además, si un control de edición es multilínea, obtener y establecer la parte del texto del control a las funciones [GetLine](../Topic/CEdit::GetLine.md), [SetSel](../Topic/CEdit::SetSel.md), [GetSel](../Topic/CEdit::GetSel.md), y [ReplaceSel](../Topic/CEdit::ReplaceSel.md)miembro de `CEdit` .  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un control de edición al elemento primario \(normalmente una clase derivada de `CDialog`\), agregue una función miembro de entrada y controlador de mensajes de mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 *Id.*de**\(**de notificación de**ON\_***, memberFxn* **\)**  
  
 donde `id` especifica el identificador de ventana secundaria del control de edición que envía la notificación, y `memberFxn` es el nombre de la función principal del miembro que ha escrito para controlar la notificación.  
  
 El prototipo de función del elemento primario es el siguiente:  
  
 memberFxn \(\);void de**afx\_msg**  
  
 A continuación se muestra una lista de entradas posibles de mapa de mensajes y una descripción de los casos en que se enviaron al elemento primario:  
  
-   El usuario de**ON\_EN\_CHANGE** The ha realizado una acción que podrían haber modificado el texto en un control de edición.  A diferencia del mensaje de notificación de **EN\_UPDATE** , se envía este mensaje de notificación cuando Windows actualizar la presentación.  
  
-   El control de edición**ON\_EN\_ERRSPACE** no puede asignar memoria suficiente para satisfacer una solicitud concreta.  
  
-   El usuario de**ON\_EN\_HSCROLL** The haga clic en la barra de desplazamiento horizontal de un control de edición.  Se notifica a la ventana primaria antes de que se actualicen a la pantalla.  
  
-   El control de edición**ON\_EN\_KILLFOCUS** The pierde el foco de entrada.  
  
-   la inserción actual de**ON\_EN\_MAXTEXT** The ha superado el número de caracteres especificado para el control de edición y se ha truncado.  También enviado cuando un control de edición no tiene el estilo de **ES\_AUTOHSCROLL** y el número de caracteres que se inserten supera el ancho del control de edición.  También enviado cuando un control de edición no tiene el estilo de **ES\_AUTOVSCROLL** y el número total de líneas el resultante de una inserción de texto supera el alto del control de edición.  
  
-   **ON\_EN\_SETFOCUS** Sent cuando un control de edición recibe el foco de entrada.  
  
-   El control de edición**ON\_EN\_UPDATE** The trata sobre el texto modificado pantalla.  Enviado después de que el control ha dado formato al texto pero antes de que se muestra el texto para poder modificar el tamaño de la ventana, si es necesario.  
  
-   El usuario de**ON\_EN\_VSCROLL** The haga clic en la barra de desplazamiento vertical de un control de edición.  Se notifica a la ventana primaria antes de que se actualicen a la pantalla.  
  
 Si crea un objeto de `CEdit` dentro de un cuadro de diálogo, el objeto de `CEdit` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CEdit` de un recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, el objeto de `CEdit` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CEdit` dentro de una ventana, puede necesitar también destruirla.  Si crea el objeto de `CEdit` en la pila, se destruye automáticamente.  Si crea el objeto de `CEdit` en la pila mediante la función de **nuevo** , debe llamar a **cancelación** en el objeto para destruirlo cuando el usuario finaliza el control de edición de Windows.  Si asigna cualquier memoria en el objeto de `CEdit` , reemplace `CEdit` destructor para destruyen las asignaciones.  
  
 Para modificar ciertos estilos de un control de edición \(como **ES\_READONLY**\) debe enviar mensajes específicos al control en lugar de utilizar [ModifyStyle](../Topic/CWnd::ModifyStyle.md).  Vea [Estilos del control de edición](http://msdn.microsoft.com/library/windows/desktop/bb775464) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre `CEdit`, vea:  
  
-   [Controles](../../mfc/controls-mfc.md)  
  
-   Caso Q259949 de Knowledge Base: INFO: SetCaretPos\(\) no Adecuado con CEdit o Controles de CRichEditCtrl  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CEdit`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo CALCDRIV de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)