---
title: "Imprimir controles Rich Edit | Microsoft Docs"
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
  - "CRichEditCtrl (clase), imprimir"
  - "imprimir [MFC], CRichEditCtrl"
  - "controles Rich Edit, imprimir"
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Imprimir controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede indicar a un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) que genera el resultado para un dispositivo especificado, como una impresora.  También puede especificar el dispositivo de salida en el que los formatos de un control de edición amplio el texto.  
  
 Para dar formato a la parte del contenido de un control rich edit para un dispositivo específico, puede utilizar la función miembro de [FormatRange](../Topic/CRichEditCtrl::FormatRange.md) .  La estructura de [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) utilizada con esta función especifica el intervalo de texto para dar formato junto con el contexto \(DC\) del dispositivo para el dispositivo de destino.  
  
 Después de que dé formato al texto para un dispositivo de salida, puede enviar la salida al dispositivo utilizando la función miembro de [DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md) .  Por repetidamente mediante `FormatRange` y `DisplayBand`, una aplicación que imprime el contenido de un control rich edit puede implementar las bandas. \(Las bandas son división de salida en partes más pequeñas para imprimirlo.\)  
  
 Puede utilizar la función miembro de [SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md) para especificar el dispositivo de destino en el que los formatos de un control de edición amplio el texto.  Esta función resulta útil para en modo WYSIWYG \(lo que se ve es lo que se obtiene\) que da formato, ya que las posiciones de una aplicación texto mediante medidas de fuente de la impresora predeterminada en lugar de la pantalla.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)