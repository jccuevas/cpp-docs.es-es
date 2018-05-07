---
title: Implementación de la barra de estado en MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13a85ba03089a9536c8c6512bccd09f1eb34c0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="status-bar-implementation-in-mfc"></a>Implementación de barra de estado en MFC
A [CStatusBar](../mfc/reference/cstatusbar-class.md) objeto es una barra de controles con una fila de paneles de salida de texto. Los paneles de salida se utilizan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos son las líneas de mensaje de Ayuda de menú que se describe brevemente el comando de menú seleccionado y los indicadores que muestran el estado de Bloq Despl, BLOQ NUM y otras claves.  
  
 A partir de la versión 4.0 de MFC, barras de estado se implementan utilizando la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), que encapsula un control común de la barra de estado. Por compatibilidad con versiones anteriores, MFC mantiene la implementación antigua de barra de estado en la clase **COldStatusBar**. Describe la documentación para las versiones anteriores de MFC **COldStatusBar** en `CStatusBar`.  
  
 [CStatusBar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), una función miembro nueva para MFC 4.0, permite aprovechar las ventajas de la compatibilidad del control común de Windows para la barra de estado personalización y funcionalidad adicional. `CStatusBar` funciones de miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetStatusBarCtrl`, puede asignar a las barras de estado aún más las características de una barra de estado. Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un `CStatusBarCtrl` objeto. Puede usar dicha referencia para manipular el control de barra de estado.  
  
 La siguiente ilustración muestra una barra de estado que muestra varios indicadores.  
  
 ![Barra de estado](../mfc/media/vc37dy1.gif "vc37dy1")  
Una barra de estado  
  
 Al igual que la barra de herramientas, el objeto de barra de estado está incrustado en su ventana de marco principal y se crea automáticamente cuando se construye la ventana de marco. La barra de estado, al igual que todas las barras de control, se destruye automáticamente también cuando se destruye el marco primario.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Actualizar el texto de un panel de barra de estado](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   Clases MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [Barras de control](../mfc/control-bars.md)  
  
-   [Barras de cuadro de diálogo](../mfc/dialog-bars.md)  
  
-   [Barras de herramientas (implementación de la barra de herramientas MFC)](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>Vea también  
 [Barras de estado](../mfc/status-bars.md)

