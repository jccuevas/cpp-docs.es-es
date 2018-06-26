---
title: Administrar ventanas secundarias MDI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MDICLIENT
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58ddef11e56da760bbecaa47f03dfa6c57dfa3ed
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929486"
---
# <a name="managing-mdi-child-windows"></a>Administrar ventanas secundarias MDI
Ventanas de marco principal MDI (una por aplicación) contienen una ventana secundaria especial denominada ventana MDICLIENT. La ventana MDICLIENT administra el área de cliente de la ventana de marco principal y tiene ventanas secundarias: las ventanas de documento, que se deriva de `CMDIChildWnd`. Dado que las ventanas de documento son ventanas de marco por sí mismos (ventanas secundarias MDI), también pueden tener sus propios elementos secundarios. En todos estos casos, la ventana primaria administra sus ventanas secundarias y reenvía algunos comandos a ellos.  
  
 En una ventana de marco MDI, la ventana de marco administra la ventana MDICLIENT, volviéndola a junto con barras de control. La ventana MDICLIENT, a su vez, administra todas las ventanas de marco secundarias MDI. En la siguiente ilustración muestra la relación entre una ventana de marco MDI, su ventana MDICLIENT y sus ventanas de marco de documento secundarias.  
  
 ![Ventanas secundarias en una ventana de marco MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Ventanas marco de MDI y ventanas secundarias  
  
 Una ventana de marco MDI también funciona junto con la ventana secundaria MDI actual, si hay alguno. La ventana de marco MDI delega mensajes de comandos en la ventana secundaria MDI antes de intentar controlarlos ella misma.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

