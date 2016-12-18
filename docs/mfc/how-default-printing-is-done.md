---
title: "C&#243;mo se realiza la impresi&#243;n predeterminada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "impresión predeterminada"
  - "predeterminados, imprimir"
  - "imprimir [MFC], predeterminada"
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo se realiza la impresi&#243;n predeterminada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica el proceso de impresión predeterminado en Windows en términos de marco de trabajo de MFC.  
  
 En aplicaciones MFC, la clase de vista tiene una función miembro denominada `OnDraw` que contiene todo el código del gráfico.  `OnDraw` contiene un puntero a un objeto de [CDC](../mfc/reference/cdc-class.md) como parámetro.  Que el objeto de `CDC` representa el contexto para recibir la imagen generada por `OnDraw`.  Cuando la ventana que muestra el documento recibe un mensaje de [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) , el marco de trabajo llama a `OnDraw` y pásele un contexto para la presentación \(un objeto de [CPaintDC](../mfc/reference/cpaintdc-class.md) , ser concreto\).  En consecuencia, el resultado de `OnDraw` va a la pantalla.  
  
 En la programación de Windows, el envío generado en la impresora es muy similar al envío generado en la pantalla.  Esto es porque la interfaz de dispositivo gráfico de Windows \(GDI\) es hardware\- independiente.  Puede utilizar las mismas funciones de GDI para la presentación en pantalla o imprimir simplemente utilizando el contexto adecuado del dispositivo.  Si el objeto de `CDC` que `OnDraw` recibe representa la impresora, el resultado de `OnDraw` va a la impresora.  
  
 Esto explica cómo las aplicaciones MFC pueden realizar la impresión simple sin requerir esfuerzo adicional de la partición.  El marco se ocupa de mostrar el cuadro de diálogo imprimir y crear un contexto para la impresora.  Cuando el usuario selecciona el comando print desde el menú archivo, la vista pasa este contexto de dispositivo a `OnDraw`, que dibuja el documento en la impresora.  
  
 Sin embargo, hay algunas diferencias significativas entre la impresión y la presentación en pantalla.  Al imprimir, es necesario dividir el documento en las páginas distintas y mostrarlas uno a la vez, en lugar de cualquier parte es visible en una ventana.  Como consecuencia natural, debe tener en cuenta el tamaño del papel \(si es tamaño de la letra, tamaño permitido, o un sobre\).  Puede que desee imprimir en distintas orientaciones, como paisaje o modo apaisado.  La biblioteca Microsoft Foundation Class no puede predecir cómo la aplicación controlará estos problemas, por lo que proporciona un protocolo para agregar estas funciones.  
  
 Ese protocolo se describe en el artículo [Documentos de varias páginas](../mfc/multipage-documents.md).  
  
## Vea también  
 [Imprimir](../mfc/printing.md)