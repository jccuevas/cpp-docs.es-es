---
title: Asignar recursos de GDI | Documentos de Microsoft
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
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef6b784a04b7be29b470b92aa09bef8bda449e2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="allocating-gdi-resources"></a>Asignar recursos de GDI
En este artículo se explica cómo asignar y desasignar los objetos de la Interfaz de dispositivo gráfico (GDI) de Windows necesarios para la impresión.  
  
> [!NOTE]
>  Para obtener más información, consulte la documentación de SDK de GDI + en: [http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 Supongamos que necesita usar determinadas fuentes, lápices u otros objetos GDI para imprimir, pero no para la visualización en pantalla. Debido a la memoria que necesitan, no resulta eficiente asignar estos objetos cuando se inicia la aplicación. Cuando la aplicación no está imprimiendo un documento, esa memoria puede ser necesaria para otros fines. Es mejor asignarlos cuando comienza la impresión y, después, eliminarlos cuando la impresión haya terminado.  
  
 Para asignar estos objetos GDI, reemplace la [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) función miembro. Esta función es apropiada para este propósito por dos razones: el marco de trabajo llama a esta función una vez al principio de cada trabajo de impresión y, a diferencia de [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), esta función tiene acceso a la [CDC](../mfc/reference/cdc-class.md) objeto que representa el controlador de dispositivo de impresora. Puede almacenar estos objetos para su uso durante el trabajo de impresión definiendo variables miembro en la clase de vista que apunten a objetos GDI (por ejemplo, **CFont \***  miembros etc.).  
  
 Para usar los objetos GDI que ha creado, selecciónelos en el contexto de dispositivo de impresora en el [OnPrint](../mfc/reference/cview-class.md#onprint) función miembro. Si necesita objetos GDI distintos para diferentes páginas del documento, puede examinar la `m_nCurPage` miembro de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) permite organizar y seleccionar el objeto GDI en consecuencia. Si necesita un objeto GDI para varias páginas consecutivas, Windows necesita que lo seleccione en el contexto de dispositivo cada vez que se llame a `OnPrint`.  
  
 Para desasignar estos objetos GDI, reemplace la [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) función miembro. El marco llama a esta función al final de cada trabajo de impresión, lo que le ofrece la oportunidad de desasignar objetos GDI específicos de impresión antes de que la aplicación vuelva a otras tareas.  
  
## <a name="see-also"></a>Vea también  
 [Imprimir](../mfc/printing.md)   
 [Cómo se realiza la impresión predeterminada](../mfc/how-default-printing-is-done.md)

