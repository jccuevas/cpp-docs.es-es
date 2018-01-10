---
title: Estilos de ventana de marco (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5bdc0204c538f476c791657d8b29a28b7baedd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-styles-c"></a>Estilos de ventana de marco (C++)
Las ventanas de marco se obtienen con el marco de trabajo son adecuadas para la mayoría de los programas, pero puede tener una flexibilidad adicional mediante las funciones avanzadas [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) y la función global de MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`es una función miembro de `CWnd`.  
  
 Si aplica el **WS_HSCROLL** y **WS_VSCROLL** estilos a la ventana de marco principal, en su lugar, se aplican a la **MDICLIENT** ventana, por lo que los usuarios puedan desplazarse la **MDICLIENT** área.  
  
 Si la ventana **FWS_ADDTOTITLE** bit de estilo está establecido (lo que sucede de forma predeterminada), la vista indica a la ventana de marco el título que se mostrará en la barra de título de la ventana según el nombre de vista documento.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Administrar ventanas secundarias MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), la ventana dentro de un marco MDI que contiene las ventanas secundarias MDI  
  
-   [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Estilos de ventana](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Vea también  
 [Ventanas de marco](../mfc/frame-windows.md)

