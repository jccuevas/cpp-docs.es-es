---
title: Imprimir | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01ee396a7866179bd140f203192d1bdcbfb4681e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="printing"></a>Impresión
Microsoft Windows implementa una presentación independientes del dispositivo. En MFC, esto significa que las mismas llamadas de dibujo, en la `OnDraw` función miembro de la clase de vista, son responsables del dibujo de la pantalla y en otros dispositivos, como las impresoras. Para la vista preliminar, el dispositivo de destino es una salida de impresora simulada para la presentación.  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>El rol en impresión frente a trabajo del marco de  
 La clase de vista tiene las siguientes responsabilidades:  
  
-   Informar a la plataforma de cuántas páginas están en el documento.  
  
-   Cuando se le pregunte para imprimir una página especificada, dibujar esa parte del documento.  
  
-   Asignar y desasignar cualquier fuente u otros recursos de interfaz (GDI) de dispositivo de gráficos necesarios para la impresión.  
  
-   Si es necesario, enviar cualquier código de escape requerido para cambiar el modo de impresora antes de imprimir una página determinada, por ejemplo, para cambiar la orientación de impresión de forma por página.  
  
 Responsabilidades del marco de trabajo son los siguientes:  
  
-   Mostrar la **impresión** cuadro de diálogo.  
  
-   Crear un [CDC](../mfc/reference/cdc-class.md) objeto de la impresora.  
  
-   Llame a la [StartDoc](../mfc/reference/cdc-class.md#startdoc) y [EndDoc](../mfc/reference/cdc-class.md#enddoc) las funciones miembro de la `CDC` objeto.  
  
-   Llamar repetidamente a la [StartPage](../mfc/reference/cdc-class.md#startpage) función miembro de la `CDC` objeto, informar a la clase de vista de página que se va a imprimir y llame a la [EndPage](../mfc/reference/cdc-class.md#endpage) función miembro de la `CDC` objeto.  
  
-   Llamar a funciones reemplazables en la vista en el momento adecuado.  
  
 Los artículos siguientes explican cómo el marco de trabajo es compatible con la impresión y la vista preliminar:  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)  
  
-   [Documentos de varias páginas](../mfc/multipage-documents.md)  
  
-   [Encabezados y pies de página](../mfc/headers-and-footers.md)  
  
-   [Asignar recursos de GDI para imprimir](../mfc/allocating-gdi-resources.md)  
  
-   [Vista previa de impresión](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>Vea también  
 [Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md)

