---
title: Funciones de miembro de Control deslizante | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3793ca47aa0537d5ca8d6858c165fc2c5ac64943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="slider-control-member-functions"></a>Funciones miembro de control deslizante
Una aplicación puede llamar el control deslizante de funciones de miembro del control para recuperar información sobre el control deslizante ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) y cambiar sus características.  
  
 Para recuperar la posición del control deslizante (es decir, el valor que el usuario ha elegido), use la [GetPos](../mfc/reference/csliderctrl-class.md#getpos) función miembro. Para establecer la posición del control deslizante, use la [SetPos](../mfc/reference/csliderctrl-class.md#setpos) función miembro. En cualquier momento puede usar el `VerifyPos` función de miembro para asegurarse de que el control deslizante está comprendida entre los valores mínimo y máximos.  
  
 El intervalo de un control deslizante es el conjunto de valores no contiguos que puede representar el control deslizante. Mayoría de aplicaciones utilizan la [SetRange](../mfc/reference/csliderctrl-class.md#setrange) función de miembro para establecer el intervalo de un control deslizante cuando se crea por primera vez. Las aplicaciones pueden modificar dinámicamente el intervalo de una vez creado el control deslizante mediante el uso de la [funciones miembro SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) y [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) funciones miembro. Una aplicación que permita el intervalo que se va a cambiarse dinámicamente normalmente recupera los valores del intervalo final cuando el usuario termina de trabajar con el control deslizante. Para recuperar estos valores, utilice la [GetRange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), y [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) funciones miembro.  
  
 Una aplicación puede utilizar el `TBS_AUTOTICKS` estilo que se va a tener marcas de graduación de un control deslizante muestra automáticamente. Si una aplicación necesita controlar la posición o la frecuencia de las marcas de graduación, sin embargo, se puede utilizar una serie de funciones de miembro.  
  
 Para establecer la posición de una marca de graduación, una aplicación puede utilizar el [SetTic](../mfc/reference/csliderctrl-class.md#settic) función miembro. El [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) función miembro permite a una aplicación establecer las marcas que aparecen a intervalos regulares en el intervalo del control deslizante de graduación. Por ejemplo, la aplicación puede utilizar esta función miembro para mostrar sólo 10 marcas de graduación de un intervalo de 1 a 100.  
  
 Para recuperar el índice en el intervalo correspondiente a una marca de graduación, use la [función miembro GetTic](../mfc/reference/csliderctrl-class.md#gettic) función miembro. El [función miembro GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) función miembro recupera una matriz de estos índices. Para recuperar la posición de una marca de graduación, en coordenadas de cliente, utilice la [función miembro GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) función miembro. Una aplicación puede recuperar el número de marcas de graduación mediante la [función miembro GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) función miembro.  
  
 El [función miembro ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) función miembro quita todas las marcas de graduación de un control deslizante.  
  
 Tamaño de la línea del control deslizante determina hasta qué punto se desplaza el control deslizante cuando una aplicación recibe un **TB_LINEDOWN** o **TB_LINEUP** mensaje de notificación. De igual forma, el tamaño de página determina la respuesta a la **TB_PAGEDOWN** y **TB_PAGEUP** mensajes de notificación. Las aplicaciones puedan recuperar y establecer los valores de tamaño de página y de línea mediante la [funciones miembro GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), y [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) funciones miembro.  
  
 Una aplicación puede utilizar las funciones miembro para recuperar las dimensiones de un control deslizante. El [función miembro GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) función miembro recupera el rectángulo delimitador para el control deslizante. El [función miembro GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) función miembro recupera el rectángulo delimitador para el canal del control deslizante. (El canal es el área que se mueve el control deslizante y que contiene el elemento resaltado cuando se selecciona un intervalo).  
  
 Si un control deslizante tiene el `TBS_ENABLESELRANGE` estilo, el usuario puede seleccionar un intervalo de valores no contiguos en él. Un número de funciones miembro permite que se ajuste dinámicamente el intervalo de selección. El [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) función miembro establece iniciales y finales de posiciones de una selección. Cuando el usuario termina de establecer un intervalo de selección, una aplicación puede recuperar la configuración mediante el [función miembro GetSelection](../mfc/reference/csliderctrl-class.md#getselection) función miembro. Para borrar la selección de un usuario, use la [función miembro ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

