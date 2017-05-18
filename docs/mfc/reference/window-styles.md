---
title: Estilos de ventana | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WS_MINIMIZEBOX
- WS_SIZEBOX
- WS_CLIPCHILDREN
- WS_TILED
- WS_GROUP
- WS_VSCROLL
- WS_CHILD
- WS_TABSTOP
- WS_HSCROLL
- WS_THICKFRAME
- WS_DISABLED
- WS_POPUP
- WS_ICONIC
- WS_MAXIMIZE
- WS_VISIBLE
- WS_POPUPWINDOW
- WS_TILEDWINDOW
- WS_DLGFRAME
- WS_MINIMIZE
- WS_CAPTION
- WS_OVERLAPPED
- WS_BORDER
- WS_MAXIMIZEBOX
- WS_OVERLAPPEDWINDOW
- WS_SYSMENU
- WS_CHILDWINDOW
- WS_CLIPSIBLINGS
dev_langs:
- C++
helpviewer_keywords:
- WS_THICKFRAME constant
- WS_TILEDWINDOW constant
- WS_MAXIMIZEBOX constant
- WS_DLGFRAME constant
- WS_CHILDWINDOW constant
- window styles, in MFC
- WS_CHILD constant
- WS_GROUP constant
- WS_MINIMIZE constant
- WS_CAPTION constant
- WS_MAXIMIZE constant
- WS_POPUP constant
- WS_SYSMENU constant
- WS_TILED constant
- window styles
- WS_POPUPWINDOW constant
- WS_CLIPSIBLINGS constant
- WS_BORDER constant
- WS_DISABLED constant
- WS_VSCROLL constant
- WS_OVERLAPPED constant
- WS_MINIMIZEBOX constant
- WS_VISIBLE constant
- WS_OVERLAPPEDWINDOW constant
- WS_TABSTOP constant
- WS_ICONIC constant
- WS_SIZEBOX constant
- WS_HSCROLL constant
- WS_CLIPCHILDREN constant
- styles, windows
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d814e3a10132fb3fe88969ce434f8286b02afba5
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="window-styles"></a>Estilos de ventana
-   `WS_BORDER`Crea una ventana que tiene un borde.  
  
-   **WS_CAPTION** crea una ventana que tiene una barra de título (implica el `WS_BORDER` estilo). No se puede usar con el **WS_DLGFRAME** estilo.  
  
-   **WS_CHILD** crea una ventana secundaria. No se puede usar con el `WS_POPUP` estilo.  
  
-   **WS_CHILDWINDOW** igual que el **WS_CHILD** estilo.  
  
-   **WS_CLIPCHILDREN** excluye el área ocupado por ventanas secundarias cuando dibuja dentro de la ventana primaria. Se utiliza al crear la ventana primaria.  
  
-   **WS_CLIPSIBLINGS** ventanas secundarias de Clips entre sí, es decir, cuando una ventana secundaria concreta recibe un mensaje de dibujo, el **WS_CLIPSIBLINGS** estilo recorta todas las demás ventanas secundarias superpuesto de fuera de la región de la ventana secundaria se actualice. (Si **WS_CLIPSIBLINGS** no tiene y secundarios windows se superponen, cuando se dibuja dentro del área cliente de una ventana secundaria, es posible dibujar dentro del área cliente de una ventana secundaria vecinas.) Para su uso con el **WS_CHILD** sólo de estilo.  
  
-   **WS_DISABLED** crea una ventana que está inicialmente deshabilitada.  
  
-   **WS_DLGFRAME** crea una ventana con un borde doble pero ningún título.  
  
-   **WS_GROUP** especifica el primer control de un grupo de controles en la que el usuario puede mover de un control a la siguiente con las teclas de dirección. Todos los controles definidos con el **WS_GROUP** estilo **FALSE** después de que el primer control pertenecen al mismo grupo. El siguiente control con el **WS_GROUP** estilo inicia el grupo siguiente (es decir, finaliza un grupo donde comienza la siguiente).  
  
-   **WS_HSCROLL** crea una ventana que tiene una barra de desplazamiento horizontal.  
  
-   **WS_ICONIC** crea una ventana que esté inicialmente minimizada. Igual que el **WS_MINIMIZE** estilo.  
  
-   **WS_MAXIMIZE** crea una ventana de tamaño máximo.  
  
-   **WS_MAXIMIZEBOX** crea una ventana que tiene un botón Maximizar.  
  
-   **WS_MINIMIZE** crea una ventana que esté inicialmente minimizada. Para su uso con el **WS_OVERLAPPED** sólo de estilo.  
  
-   **WS_MINIMIZEBOX** crea una ventana que tiene un botón Minimizar.  
  
-   **WS_OVERLAPPED** crea una ventana superpuesta. Normalmente, una ventana superpuesta tiene un título y un borde.  
  
-   **WS_OVERLAPPEDWINDOW** crea una ventana superpuesta con el **WS_OVERLAPPED**, **WS_CAPTION**, **WS_SYSMENU**, **WS_THICKFRAME**, **WS_MINIMIZEBOX**, y **WS_MAXIMIZEBOX** estilos.  
  
-   `WS_POPUP`Crea una ventana emergente. No se puede usar con el **WS_CHILD** estilo.  
  
-   **WS_POPUPWINDOW** crea una ventana emergente con la `WS_BORDER`, `WS_POPUP`, y **WS_SYSMENU** estilos. El **WS_CAPTION** estilo debe combinarse con la **WS_POPUPWINDOW** estilos para hacer visible el menú Control.  
  
-   **WS_SIZEBOX** crea una ventana que tiene un borde de tamaño. Igual que el **WS_THICKFRAME** estilo.  
  
-   **WS_SYSMENU** crea una ventana que tiene un cuadro de menú Control en la barra de título. Se utiliza sólo para windows con barras de título.  
  
-   **WS_TABSTOP** especifica cualquier número de controles a través del cual el usuario puede mover mediante la tecla TAB. La tecla TAB mueve el usuario al siguiente control especificado por la **WS_TABSTOP** estilo.  
  
-   **WS_THICKFRAME** crea una ventana con un marco grueso que puede utilizarse para cambiar el tamaño de la ventana.  
  
-   **WS_TILED** crea una ventana superpuesta. Una ventana superpuesta tiene una barra de título y un borde. Igual que el **WS_OVERLAPPED** estilo.  
  
-   **WS_TILEDWINDOW** crea una ventana superpuesta con el **WS_OVERLAPPED**, **WS_CAPTION**, **WS_SYSMENU**, **WS_THICKFRAME**, **WS_MINIMIZEBOX**, y **WS_MAXIMIZEBOX** estilos. Igual que el **WS_OVERLAPPEDWINDOW** estilo.  
  
-   **WS_VISIBLE** crea una ventana que esté visible inicialmente.  
  
-   **WS_VSCROLL** crea una ventana que tiene una barra de desplazamiento vertical.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create)   
 [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)   
 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)


