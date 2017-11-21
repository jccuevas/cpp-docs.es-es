---
title: Clases de ventana (arquitectura) de marco | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.frame
dev_langs: C++
helpviewer_keywords: frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b4a8076cbec9292718c9bc2413d690bacbc4a67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="frame-window-classes-architecture"></a>Clases de ventana de marco (Arquitectura)
En la arquitectura documento/vista, ventanas de marco son ventanas que contienen una ventana de vista. También admiten tener control barras asociadas a ellos.  
  
 En aplicaciones de múltiples documentos (MDI) de la interfaz, se deriva de la ventana principal `CMDIFrameWnd`. Indirectamente contiene marcos de los documentos, que son `CMDIChildWnd` objetos. El `CMDIChildWnd` objetos, a su vez, contienen vistas de los documentos.  
  
 En las aplicaciones de único documento (SDI) de la interfaz, la ventana principal, se deriva de `CFrameWnd`, contiene la vista del documento actual.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación MDI.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 La clase base para ventanas de marco de documento de una aplicación MDI.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana de marco para obtener una vista cuando se está editando un documento del servidor en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

