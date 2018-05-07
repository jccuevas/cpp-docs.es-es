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
ms.openlocfilehash: edcdcbad2b7b3e70988579786c1c8cf28f734a48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="managing-mdi-child-windows"></a>Administrar ventanas secundarias MDI
Ventanas de marco principal MDI (una por aplicación) contienen una ventana secundaria especial denominada el **MDICLIENT** ventana. El **MDICLIENT** ventana administra el área de cliente de la ventana de marco principal y tiene ventanas secundarias: las ventanas de documento, que se deriva de `CMDIChildWnd`. Dado que las ventanas de documento son ventanas de marco por sí mismos (ventanas secundarias MDI), también pueden tener sus propios elementos secundarios. En todos estos casos, la ventana primaria administra sus ventanas secundarias y reenvía algunos comandos a ellos.  
  
 En una ventana de marco MDI, la ventana de marco administra la **MDICLIENT** ventana, volviéndola a junto con barras de control. El **MDICLIENT** ventana, a su vez, administra todas las ventanas de marco secundarias MDI. En la siguiente ilustración se muestra la relación entre una ventana de marco MDI, su **MDICLIENT** ventana y sus ventanas de marco de documento secundarias.  
  
 ![Ventanas secundarias en una ventana de marco MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Ventanas marco de MDI y ventanas secundarias  
  
 Una ventana de marco MDI también funciona junto con la ventana secundaria MDI actual, si hay alguno. La ventana de marco MDI delega mensajes de comandos en la ventana secundaria MDI antes de intentar controlarlos ella misma.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

