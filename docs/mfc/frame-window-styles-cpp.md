---
title: Estilos de ventana de marco (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102b3a4c8372a53aada23ad448ce5dc1cf323a97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343766"
---
# <a name="frame-window-styles-c"></a>Estilos de ventana de marco (C++)
Las ventanas de marco se obtienen con el marco de trabajo son adecuadas para la mayoría de los programas, pero puede tener una flexibilidad adicional mediante las funciones avanzadas [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) y la función global de MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` es una función miembro de `CWnd`.  
  
 Si aplica el **WS_HSCROLL** y **WS_VSCROLL** estilos a la ventana de marco principal, en su lugar, se aplican a la **MDICLIENT** ventana, por lo que los usuarios puedan desplazarse la **MDICLIENT** área.  
  
 Si la ventana **FWS_ADDTOTITLE** bit de estilo está establecido (lo que sucede de forma predeterminada), la vista indica a la ventana de marco el título que se mostrará en la barra de título de la ventana según el nombre de vista documento.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Administrar ventanas secundarias MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), la ventana dentro de un marco MDI que contiene las ventanas secundarias MDI  
  
-   [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Estilos de ventana](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Vea también  
 [Ventanas de marco](../mfc/frame-windows.md)

