---
title: "Arquitectura de la vista previa de impresi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vista previa de impresión"
  - "vista previa de impresión, arquitectura"
  - "vista previa de impresión, modificaciones en MFC"
  - "vista previa de impresión, proceso"
  - "imprimir [MFC], vista previa de impresión"
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Arquitectura de la vista previa de impresi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo el marco de trabajo de MFC implementa la funcionalidad de vista previa de impresión.  Entre los temas tratados, se incluyen los siguientes:  
  
-   [Proceso de vista previa de impresión](#_core_the_print_preview_process)  
  
-   [Vista previa de impresión de modificación](#_core_modifying_print_preview)  
  
 La vista previa de impresión es ligeramente distinto de presentación en pantalla y de impresión porque, en lugar directamente de dibujar una imagen en un dispositivo, la aplicación debe simular la impresora mediante la pantalla.  Para ello, la biblioteca Microsoft Foundation Class define una clase \(indocumentada\) especial derivada de [CDC \(clase\)](../mfc/reference/cdc-class.md), denominado **CPreviewDC**.  Todos los objetos de `CDC` contienen dos contextos de dispositivo, pero normalmente son idénticos.  En un objeto de **CPreviewDC** , son diferentes: el primer representa la impresora que se simula, y el segundo representa en la pantalla donde se muestra la salida realmente.  
  
##  <a name="_core_the_print_preview_process"></a> El proceso de vista previa de impresión  
 Cuando el usuario selecciona el comando de vista previa de impresión de menú de **archivo** , el marco de trabajo crea un objeto de **CPreviewDC** .  Siempre que la aplicación realice una operación que establezca una característica de contexto de dispositivo de impresora, el marco de trabajo también realiza una operación similar en el contexto del dispositivo de pantalla.  Por ejemplo, si la aplicación selecciona una fuente para imprimir, el marco selecciona una fuente para la presentación en pantalla que simula a la fuente de impresora.  Siempre que la aplicación enviara el resultado en la impresora, el marco en su lugar envía los resultados a la pantalla.  
  
 La vista previa de impresión también difiere de la impresión en el orden en el que cada dibuja las páginas de un documento.  Durante la impresión, el marco continúa un bucle de impresión hasta que se haya generado un intervalo de páginas.  Durante la vista previa de impresión, uno o dos páginas se muestran en cualquier momento, y a continuación la aplicación espera; no se muestra ninguna otras páginas hasta que el usuario.  Durante la vista previa de impresión, la aplicación también debería responder a los mensajes de `WM_PAINT` , al igual que durante presentación en pantalla normal.  
  
 Se llama a la función de [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) cuando se invoca el modo de vista previa, exactamente igual que al principio de un trabajo de impresión.  La estructura de [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) pasada a la función contiene varios miembros cuyos valores se puede establecer para ajustar ciertas características de la operación de la vista previa de impresión.  Por ejemplo, puede establecer el miembro de **m\_nNumPreviewPages** para especificar si desea obtener una vista previa del documento en modo de una página o la dos\- página.  
  
##  <a name="_core_modifying_print_preview"></a> Vista previa de impresión de modificación  
 Puede modificar el comportamiento y la apariencia de la vista previa de impresión de varias maneras en lugar fácilmente.  Por ejemplo, puede, entre otras cosas:  
  
-   Haga la ventana de vista previa para mostrar una barra de desplazamiento para facilitar el acceso a cualquier página del documento.  
  
-   Haga la vista previa de impresión para mantener la posición del usuario en el documento iniciando la presentación de la página actual.  
  
-   Produce diferente inicialización que se va a realizar para la vista previa de impresión y la impresión.  
  
-   Hace que la vista previa de impresión a los números de página de presentación de los propios formatos.  
  
 Si sabe cuánto tiempo el documento es y llama a `SetMaxPage` con el valor adecuado, el marco puede utilizar esta información en el modo de vista previa así como durante la impresión.  Una vez que el marco conoce la longitud del documento, puede proporcionar la ventana de vista previa con una barra de desplazamiento, permitiendo al usuario a la página de uno a otro a través del documento en modo de vista previa.  Si no ha establecido la longitud del documento, el marco no puede colocar el cuadro de desplazamiento para indicar la posición actual, por lo que el marco no agrega una barra de desplazamiento.  En este caso, el usuario debe utilizar los botones siguientes de la página y la página Anteriores de en la barra de control de la ventana de vista previa a la página a través del documento.  
  
 Para la vista previa de impresión, puede resultarle útil para asignar un valor al miembro de `m_nCurPage` de `CPrintInfo`, aunque no haría en la impresión normal.  Durante la impresión ordinaria, este miembro contiene la información del marco a la clase de vista.  Así es cómo el marco indica a vista qué página debe ser impresa.  
  
 Por el contrario, cuando se inicia el modo vista previa de impresión, el miembro de `m_nCurPage` transporta información en la dirección contraria: de la vista al marco.  El marco de trabajo usa el valor de este miembro para determinar qué página se debe obtener una vista previa de primero.  El valor predeterminado de este miembro es 1, lo que la primera página del documento se muestra inicialmente.  Puede reemplazar `OnPreparePrinting` para establecer este miembro el número de la página que es la vista cuando se invocó el comando de vista previa de impresión.  De esta manera, la aplicación mantiene la posición actual del usuario al pasar del modo de presentación normal al modo de vista previa de impresión.  
  
 Puede que a veces `OnPreparePrinting` para realizar diferente inicialización dependiendo de si se denomina para un trabajo de impresión o para la vista previa de impresión.  Puede determinar esto examinando a la variable miembro de **m\_bPreview** en la estructura de `CPrintInfo` .  Establecen este miembro a **VERDADERO** cuando se invoca la vista previa de impresión.  
  
 La estructura de `CPrintInfo` también contiene un miembro denominado **m\_strPageDesc**, que se utiliza para dar formato a cadenas mostradas en la parte inferior de la pantalla en modos de la solo\- página y la múltiple\- página.  De forma predeterminada las cadenas se “ *n*de página” del formulario y “ *n*de páginas   \- *m*,” pero puede modificar **m\_strPageDesc** dentro de `OnPreparePrinting` y establecer las cadenas algo más preparado.  Vea [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) en *la referencia de MFC* para obtener más información.  
  
## Vea también  
 [Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)   
 [Imprimir](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC \(clase\)](../mfc/reference/cdc-class.md)