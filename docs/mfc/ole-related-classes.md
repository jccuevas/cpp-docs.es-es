---
title: Clases relacionadas con OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4cb40e237eb6197dfe7e0cf944f12d25ca0e28e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-related-classes"></a>Clases relacionadas con OLE
Estas clases proporcionan varios servicios diferentes, que van desde las excepciones en el archivo de entrada y salida.  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 Se utiliza para crear elementos cuando se solicita de otros contenedores. Esta clase actúa como clase base para los tipos más específicos de generadores, incluidos los `COleTemplateServer`.  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 Se utiliza para administrar la simultaneidad con OLE ligero remoto procedimiento llamadas (LRPC).  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utiliza el COM `IStream` interfaz para proporcionar `CFile` acceso a archivos compuestos. Esta clase (derivado de `CFile`) habilita la serialización de MFC usar el almacenamiento estructurado OLE.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Se utiliza para permitir mover, cambiar el tamaño y reorientación de elementos en contexto.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

