---
title: "Imprimir | Microsoft Docs"
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
  - "documentos, imprimir"
  - "imprimir [MFC]"
  - "imprimir [MFC], de framework"
  - "clases de vista, operaciones de impresión"
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Imprimir
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Windows implementa la pantalla independientes del dispositivo.  En MFC, esto significa que las mismas llamadas de dibujo, en la función miembro de `OnDraw` de la clase de vista, son responsables de dibujar en pantalla y en otros dispositivos, como impresoras.  Para la vista previa de impresión, el dispositivo de destino es una salida simulada de la impresora en la pantalla.  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> El rol en la impresión en el rol de marco  
 La clase de vista tiene las siguientes responsabilidades:  
  
-   Informe al marco cuántas páginas están en el documento.  
  
-   Cuando se le imprimir una página concreta, dibuje a ese elemento.  
  
-   Asignar y desasignar cualquier espacio cualquier fuente u otros recursos de \(GDI\) de la interfaz de dispositivo gráfico necesarios para imprimir.  
  
-   Si es necesario, envíe cualquier código de escape necesario para cambiar el modo impresora antes de imprimir una página determinada, por ejemplo, para cambiar la orientación de la impresión en función de la por\- página.  
  
 Las responsabilidades de marco son como sigue:  
  
-   Muestre el cuadro de diálogo de **Impresión** .  
  
-   Cree un objeto de [CDC](../mfc/reference/cdc-class.md) para la impresora.  
  
-   Llame a las funciones miembro de [StartDoc](../Topic/CDC::StartDoc.md) y de [EndDoc](../Topic/CDC::EndDoc.md) del objeto de `CDC` .  
  
-   Llame a repetidamente la función miembro de [StartPage](../Topic/CDC::StartPage.md) del objeto de `CDC` , informan a la clase de vista qué página debe ser impresa, y llama a la función miembro de [EndPage](../Topic/CDC::EndPage.md) del objeto de `CDC` .  
  
-   Llame a las funciones overridable en la vista en los tiempos adecuados.  
  
 Los artículos siguientes explican cómo el marco admite la impresión y vista previa de impresión:  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Cómo predeterminados se hace la impresión](../mfc/how-default-printing-is-done.md)  
  
-   [Documentos de varias páginas](../mfc/multipage-documents.md)  
  
-   [Encabezados y pies de página](../mfc/headers-and-footers.md)  
  
-   [Asignar recursos de GDI para imprimir](../mfc/allocating-gdi-resources.md)  
  
-   [Vista previa de impresión](../mfc/print-preview-architecture.md)  
  
## Vea también  
 [Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)