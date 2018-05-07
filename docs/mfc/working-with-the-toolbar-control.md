---
title: Trabajar con el Control de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32d3cc6244bc2f928c8d1d0c6e46d1bc5a57aa3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-the-toolbar-control"></a>Trabajar con el control ToolBar
Este artículo explica cómo puede tener acceso a la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto subyacente un [CToolBar](../mfc/reference/ctoolbar-class.md) para un mayor control sobre las barras de herramientas. Se trata de un tema avanzado.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Para obtener acceso al control común de barra de herramientas subyacente al objeto CToolBar.  
  
1.  Llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).  
  
 `GetToolBarCtrl` Devuelve una referencia a un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto. Puede usar dicha referencia para llamar a funciones miembro de la clase de control de barra de herramientas.  
  
> [!CAUTION]
>  Mientras se llama `CToolBarCtrl` **obtener** funciones es segura, tenga cuidado si se llama a la **establecer** funciones. Se trata de un tema avanzado. Normalmente no es necesario tener acceso al control de barra de herramientas subyacente.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Controles (controles comunes de Windows)](../mfc/controls-mfc.md)  
  
-   [Aspectos básicos de la barra de herramientas](../mfc/toolbar-fundamentals.md)  
  
-   [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)  
  
-   [Cambiar el tamaño de la barra de herramientas dinámicamente](../mfc/docking-and-floating-toolbars.md)  
  
-   [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   [Actualizaciones de barra de estado por proximidad](../mfc/toolbar-tool-tips.md)  
  
-   [Controlar las notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md)  
  
-   El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases  
  
-   [Controlar notificaciones de personalización](../mfc/handling-customization-notifications.md)  
  
-   [Varias barras de herramientas](../mfc/toolbar-fundamentals.md)  
  
-   [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
-   [Barras de control](../mfc/control-bars.md)  
  
 Para obtener información general sobre el uso de controles comunes de Windows, vea [controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

