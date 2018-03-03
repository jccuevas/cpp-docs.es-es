---
title: Desplazar y escalar vistas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8bd42a7da91f984c4cedc4deafc0ab9f4417495
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-and-scaling-views"></a>Desplazar y escalar vistas
MFC admite vistas que se desplazan y visualizan que se escalan automáticamente al tamaño de la ventana de marco que mostrarlos. Clase `CScrollView` admite ambos tipos de vistas.  
  
 Para obtener más información acerca de desplazar y escalar, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en el *referencia de MFC*. Para obtener un ejemplo de desplazamiento, vea el [ejemplo Scribble](../visual-cpp-samples.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   Desplazamiento de una vista  
  
-   Ajuste de escala de una vista  
  
-   [Coordenadas de la vista](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a>Desplazamiento de una vista  
 Con frecuencia el tamaño de un documento es mayor que el tamaño que se puede mostrar la vista. Esto puede ocurrir porque los datos del documento aumentan o reduce la ventana que contiene la vista de usuario. En tales casos, la vista debe admite el desplazamiento.  
  
 Cualquier vista puede controlar los mensajes de la barra de desplazamiento en su `OnHScroll` y `OnVScroll` funciones miembro. Puede hacer todo el trabajo usted mismo cualquier control de mensajes de la barra de desplazamiento de implementar en estas funciones, o puede usar el `CScrollView` clase para controlar el desplazamiento por usted.  
  
 `CScrollView` hace lo siguiente:  
  
-   Administra los tamaños de ventana y el área de visualización y modos de asignación.  
  
-   Se desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento  
  
 Puede especificar la cantidad de desplazamiento de una "página" (cuando el usuario hace clic en un eje de una barra de desplazamiento) y una "línea" (cuando el usuario hace clic en una flecha de desplazamiento). Planear estos valores para adaptarlo a la naturaleza de la vista. Por ejemplo, puede desplazarse en incrementos de 1 píxel para una vista de gráficos, pero en incrementos basados en el alto de línea en documentos de texto.  
  
##  <a name="_core_scaling_a_view"></a>Ajuste de escala de una vista  
 Si desea que la vista para ajustar automáticamente el tamaño de su ventana de marco, puede usar `CScrollView` para ajustar la escala en lugar de desplazarse. La vista lógica se expandirán o comprimirán para ajustarse exactamente a área de cliente de la ventana. Una vista con escala no tiene barras de desplazamiento.  
  
## <a name="see-also"></a>Vea también  
 [Uso de vistas](../mfc/using-views.md)

