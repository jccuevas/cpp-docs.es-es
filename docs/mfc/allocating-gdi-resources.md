---
title: "Asignar recursos de GDI | Microsoft Docs"
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
  - "objetos GDI, asignar durante la impresión"
  - "imprimir [MFC], asignar recursos de GDI"
  - "recursos [MFC], imprimir"
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asignar recursos de GDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo asignar y desasignar los objetos de la Interfaz de dispositivo gráfico \(GDI\) de Windows necesarios para la impresión.  
  
> [!NOTE]
>  GDI\+ se incluye con Windows XP y está disponible como componente redistribuible para Windows NT 4.0 SP6, Windows 2000, Windows 98 y Windows Millennium Edition.  Para descargar el último componente redistribuible, vea [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm).  Para más información, vea la documentación del SDK de GDI\+ en MSDN: [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp).  
  
 Supongamos que necesita usar determinadas fuentes, lápices u otros objetos GDI para imprimir, pero no para la visualización en pantalla.  Debido a la memoria que necesitan, no resulta eficiente asignar estos objetos cuando se inicia la aplicación.  Cuando la aplicación no está imprimiendo un documento, esa memoria puede ser necesaria para otros fines.  Es mejor asignarlos cuando comienza la impresión y, después, eliminarlos cuando la impresión haya terminado.  
  
 Para asignar estos objetos GDI, reemplace la función miembro [OnBeginPrinting](../Topic/CView::OnBeginPrinting.md).  Esta función es apropiada para este propósito por dos razones: el marco llama a esta función una vez al principio de cada trabajo de impresión y, a diferencia de [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md), esta función tiene acceso al objeto [CDC](../mfc/reference/cdc-class.md) objeto que representa el controlador de dispositivo de impresora.  Puede almacenar estos objetos para su uso durante el trabajo de impresión definiendo en la clase de vista variables miembro que apunten a objetos GDI \(por ejemplo, miembros **CFont \***, etc.\).  
  
 Para usar los objetos GDI que ha creado, selecciónelos en el contexto de dispositivo de impresora de la función miembro [OnPrint](../Topic/CView::OnPrint.md).  Si necesita objetos GDI distintos para diferentes páginas del documento, puede examinar el miembro `m_nCurPage` de la estructura [CPrintInfo](../mfc/reference/cprintinfo-structure.md) y seleccionar el objeto GDI en consecuencia.  Si necesita un objeto GDI para varias páginas consecutivas, Windows necesita que lo seleccione en el contexto de dispositivo cada vez que se llame a `OnPrint`.  
  
 Para desasignar estos objetos GDI, reemplace la función miembro [OnBeginPrinting](../Topic/CView::OnEndPrinting.md).  El marco llama a esta función al final de cada trabajo de impresión, lo que le ofrece la oportunidad de desasignar objetos GDI específicos de impresión antes de que la aplicación vuelva a otras tareas.  
  
## Vea también  
 [Imprimir](../mfc/printing.md)   
 [Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)