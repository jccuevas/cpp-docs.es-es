---
title: "Arquitectura de vista previa de impresión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 49ddbc29762ea07cf1f7b5fa24fafd3cfa5e8612
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="print-preview-architecture"></a>Arquitectura de la vista previa de impresión
Este artículo explica cómo el marco de trabajo MFC implementa la funcionalidad de vista previa de impresión. Los temas tratados son:  
  
-   [Proceso de vista previa de impresión](#_core_the_print_preview_process)  
  
-   [Modificar la vista previa de impresión](#_core_modifying_print_preview)  
  
 Vista previa de impresión es ligeramente distinto en pantalla y la impresión porque, en lugar de dibujar directamente una imagen en un dispositivo, la aplicación debe simular la impresora con la pantalla. Para dar cabida a esto, la biblioteca Microsoft Foundation Class define una clase de (sin documentar) especial derivada de [CDC (clase)](../mfc/reference/cdc-class.md), llamado **CPreviewDC**. Todos los `CDC` objetos contienen dos contextos de dispositivo, pero normalmente son idénticos. En un **CPreviewDC** objeto, son diferentes: el primero representa la impresora simulada y el segundo representa la pantalla en el que realmente se muestra el resultado.  
  
##  <a name="_core_the_print_preview_process"></a>El proceso de vista previa de impresión  
 Cuando el usuario selecciona el comando Vista previa de impresión desde el **archivo** menú, el marco de trabajo crea un **CPreviewDC** objeto. Cada vez que la aplicación realiza una operación que establece una característica del contexto de dispositivo de impresora, el marco de trabajo también realiza una operación similar en el contexto de dispositivo de pantalla. Por ejemplo, si la aplicación selecciona una fuente para la impresión, el marco de trabajo selecciona una fuente de pantalla que simula la fuente de impresora. Cada vez que la aplicación envía resultados a la impresora, el marco de trabajo en su lugar, envía el resultado a la pantalla.  
  
 Vista previa de impresión también difiere de la impresión en el orden en que cada una dibuja las páginas de un documento. Durante la impresión, el marco de trabajo continúa un bucle de impresión hasta que se ha procesado un determinado intervalo de páginas. Durante la vista previa de impresión, una o dos páginas se muestran en cualquier momento y, a continuación, la aplicación espera; No hay más páginas se muestran hasta que el usuario responde. Durante la vista previa de impresión, la aplicación también debe responder a `WM_PAINT` mensajes, igual que durante la presentación en pantalla ordinaria.  
  
 El [CView:: OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) función se llama cuando se invoca el modo de vista previa, igual que al principio de un trabajo de impresión. El [CPrintInfo (estructura)](../mfc/reference/cprintinfo-structure.md) estructura pasada a la función contiene varios miembros cuyos valores se pueden establecer para ajustar ciertas características de la operación de vista previa de impresión. Por ejemplo, puede establecer la **m_nNumPreviewPages** miembro para especificar si desea obtener una vista previa del documento en modo de una página o dos páginas.  
  
##  <a name="_core_modifying_print_preview"></a>Modificar la vista previa de impresión  
 Puede modificar el comportamiento y la apariencia de la vista previa de impresión de varias maneras de fácilmente en su lugar. Por ejemplo, puede, entre otras cosas:  
  
-   Hace que la ventana de vista previa de impresión mostrar una barra de desplazamiento para facilitar el acceso a cualquier página del documento.  
  
-   Hacer que la vista preliminar para mantener la posición del usuario en el documento mediante el comienzo de su presentación en la página actual.  
  
-   Provocar una inicialización distinta que realizar para la impresión y vista previa de impresión.  
  
-   Hacer que la vista preliminar para mostrar los números de página en su propio formato.  
  
 Si sabe cuánto tiempo el documento y se llama `SetMaxPage` con el valor adecuado, el marco de trabajo puede usar esta información en modo de vista previa, así como durante la impresión. Una vez que el marco de trabajo conoce la longitud del documento, puede proporcionar la ventana de vista previa con una barra de desplazamiento, que permite al usuario a la página y hacia atrás a través del documento en modo de vista previa. Si no ha establecido la longitud del documento, el marco de trabajo no puede situar el cuadro de desplazamiento para indicar la posición actual, por lo que el marco de trabajo no agrega una barra de desplazamiento. En este caso, el usuario debe utilizar los botones de página anterior y página siguiente en la barra de control de la ventana de vista previa para paginar a través del documento.  
  
 Para la vista previa de impresión, quizá le resulte útil asignar un valor a la `m_nCurPage` miembro de `CPrintInfo`, incluso aunque nunca debería hacerlo para la impresión normal. Durante la impresión ordinaria, este miembro transporta información desde el marco de trabajo para la clase de vista. Se trata cómo el marco de trabajo indica a la vista de página que se debe imprimir.  
  
 Por el contrario, cuando se inicia el modo de vista previa de impresión, el `m_nCurPage` miembro transporta información en dirección opuesta: desde la vista para el marco de trabajo. El marco de trabajo usa el valor de este miembro para determinar qué página se debe mostrar en primer lugar. El valor predeterminado de este miembro es 1, por lo que se muestra inicialmente la primera página del documento. Puede invalidar `OnPreparePrinting` para establecer este miembro en el número de la página que se visualiza en el momento en que se invocó el comando Vista previa de impresión. De esta manera, la aplicación mantiene la posición del usuario actual al pasar de modo de presentación normal a modo de vista previa de impresión.  
  
 En ocasiones, puede que desee `OnPreparePrinting` para realizar la inicialización diferente dependiendo de si se llama para un trabajo de impresión o de vista previa de impresión. Se puede determinar examinando la **m_bPreview** variable miembro en el `CPrintInfo` estructura. Este miembro está establecido en **TRUE** cuando se invoque la vista previa de impresión.  
  
 El `CPrintInfo` estructura también contiene un miembro denominado **m_strPageDesc**, que se usa para dar formato a las cadenas que se muestran en la parte inferior de la pantalla en los modos de página y de varias páginas. De forma predeterminada, estas cadenas son del tipo "página  *n* " y "páginas  *n*   -  *m*," pero se pueden modificar **m_ strPageDesc** desde `OnPreparePrinting` y establezca las cadenas en algo más elaborados. Vea [CPrintInfo (estructura)](../mfc/reference/cprintinfo-structure.md) en el *referencia de MFC* para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)   
 [Imprimir](../mfc/printing.md)   
 [CView (clase)](../mfc/reference/cview-class.md)   
 [CDC (clase)](../mfc/reference/cdc-class.md)
