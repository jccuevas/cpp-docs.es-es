---
title: Clases de ventana (Windows) de marco | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.frame
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2668a8334192d4de199f1c42a648b74add1ca5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes-windows"></a>Clases de ventana de marco (Windows)
Ventanas de marco son ventanas que una aplicación o una parte de una aplicación de marco. Ventanas de marco suelen contengan otras ventanas, como vistas, barras de herramientas y barras de estado. En el caso de `CMDIFrameWnd`, que pueden contener `CMDIChildWnd` objetos indirectamente.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación MDI.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 La clase base para ventanas de marco de documento de una aplicación MDI.  
  
 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)  
 Una ventana de marco de altura media suelen ver alrededor de barras de herramientas flotantes.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana de marco para obtener una vista cuando se está editando un documento del servidor en su lugar.  
  
## <a name="related-class"></a>Clase relacionada  
 Clase `CMenu` proporciona una interfaz a través de la que se va a obtener acceso a los menús de la aplicación. Es útil para manipular menús dinámicamente en tiempo de ejecución; Por ejemplo, al agregar o eliminar elementos de menú según el contexto. Aunque los menús se suelen usar con ventanas de marco, también puede utilizar con cuadros de diálogo y en otras ventanas no secundaria.  
  
 [CMenu](../mfc/reference/cmenu-class.md)  
 Encapsula un `HMENU` identificador de la aplicación de la barra de menús y menús emergentes.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

