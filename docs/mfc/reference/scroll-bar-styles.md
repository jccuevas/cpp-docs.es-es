---
title: Estilos de barra de desplazamiento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SBS_VERT
- SBS_SIZEBOXBOTTOMRIGHTALIGN
- SBS_LEFTALIGN
- SBS_RIGHTALIGN
- SBS_TOPALIGN
- SBS_SIZEBOXTOPLEFTALIGN
- SBS_BOTTOMALIGN
- SBS_SIZEBOX
- SBS_HORZ
dev_langs:
- C++
helpviewer_keywords:
- SBS_HORZ constant
- SBS_TOPALIGN constant
- SBS_SIZEBOX constant
- SBS_BOTTOMALIGN constant
- SBS_VERT constant
- SBS_LEFTALIGN constant
- SBS_SIZEBOXBOTTOMRIGHTALIGN constant
- scroll bars, styles
- SBS_SIZEBOXTOPLEFTALIGN constant
- SBS_RIGHTALIGN constant
ms.assetid: 8bcde35b-387d-49ae-bdd6-7cda9f5dae26
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
ms.openlocfilehash: 778fe7b0f6f6319884df4ed9c5ccbe8e34bd8d42
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="scroll-bar-styles"></a>Estilos de barra de desplazamiento
-   **SBS_BOTTOMALIGN** se utiliza con la **SBS_HORZ** estilo. El borde inferior de la barra de desplazamiento se alinea con el borde inferior del rectángulo especificado en el **crear** función miembro. La barra de desplazamiento tiene el alto predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS_HORZ** designa una barra de desplazamiento horizontal. Si no la **SBS_BOTTOMALIGN** ni **SBS_TOPALIGN** se especifica el estilo, la barra de desplazamiento tiene el alto, el ancho y la posición en la **crear** función miembro.  
  
-   **SBS_LEFTALIGN** se utiliza con la **SBS_VERT** estilo. El borde izquierdo de la barra de desplazamiento se alinea con el borde izquierdo del rectángulo especificado en el **crear** función miembro. La barra de desplazamiento tiene el ancho predeterminado de las barras de desplazamiento del sistema.  
  
-   **SBS_RIGHTALIGN** se utiliza con la **SBS_VERT** estilo. El borde derecho de la barra de desplazamiento se alinea con el borde derecho del rectángulo especificado en el **crear** función miembro. La barra de desplazamiento tiene el ancho predeterminado de las barras de desplazamiento del sistema.  
  
-   **SBS_SIZEBOX** designa un cuadro de tamaño. Si no la **SBS_SIZEBOXBOTTOMRIGHTALIGN** ni **SBS_SIZEBOXTOPLEFTALIGN** se especifica el estilo, el cuadro de tamaño tiene el alto, el ancho y la posición de la **crear** función miembro.  
  
-   **SBS_SIZEBOXBOTTOMRIGHTALIGN** se utiliza con la **SBS_SIZEBOX** estilo. La esquina inferior derecha del cuadro de tamaño se alinea con la esquina inferior derecha del rectángulo especificado en el **crear** función miembro. El cuadro de tamaño tiene el tamaño predeterminado para los cuadros de tamaño del sistema.  
  
-   **SBS_SIZEBOXTOPLEFTALIGN** se utiliza con la **SBS_SIZEBOX** estilo. La esquina superior izquierda del cuadro de tamaño se alinea con la esquina superior izquierda del rectángulo especificado en el **crear** función miembro. El cuadro de tamaño tiene el tamaño predeterminado para los cuadros de tamaño del sistema.  
  
-   **SBS_SIZEGRIP** igual que **SBS_SIZEBOX**, pero con un borde en relieve.  
  
-   **SBS_TOPALIGN** se utiliza con la **SBS_HORZ** estilo. El borde superior de la barra de desplazamiento se alinea con el borde superior del rectángulo especificado en el **crear** función miembro. La barra de desplazamiento tiene el alto predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS_VERT** designa una barra de desplazamiento vertical. Si no la **SBS_RIGHTALIGN** ni **SBS_LEFTALIGN** se especifica el estilo, la barra de desplazamiento tiene el alto, el ancho y la posición en la **crear** función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CScrollBar::Create](../../mfc/reference/cscrollbar-class.md#create)   
 [Estilos de Control de barra de desplazamiento](http://msdn.microsoft.com/library/windows/desktop/bb787533)


