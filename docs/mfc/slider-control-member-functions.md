---
title: "Funciones miembro de control deslizante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl (clase), métodos"
  - "controles deslizantes, funciones miembro"
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Funciones miembro de control deslizante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación puede llamar a las funciones miembro del control deslizante para recuperar información sobre el control deslizante \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) y cambiar sus características.  
  
 Para recuperar la posición del control deslizante \(es decir, el valor que el usuario ha elegido\), utilice la función miembro de [GetPos](../Topic/CSliderCtrl::GetPos.md) .  Para establecer la posición del control deslizante, utilice la función miembro de [SetPos](../Topic/CSliderCtrl::SetPos.md) .  Puede utilizar en cualquier momento la función miembro de `VerifyPos` para asegurarse de que el control deslizante está entre los valores mínimo y máximo.  
  
 El intervalo de un control deslizante es el conjunto de valores contiguos que el control deslizante puede representar.  La mayoría de las aplicaciones utilizan la función miembro de [SetRange](../Topic/CSliderCtrl::SetRange.md) para establecer el intervalo de un control deslizante cuando se crea por primera vez.  Las aplicaciones pueden modificar dinámicamente el intervalo después del control deslizante se han creado mediante [SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md) y el miembro de [SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md) funciona.  Una aplicación que permite que el intervalo se modifique dinámicamente normalmente recupera los valores finales de intervalo cuando el usuario ha terminado de trabajar con el control deslizante.  Para recuperar estos valores, utilice [GetRange](../Topic/CSliderCtrl::GetRange.md), [GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md), y el miembro de [GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md) funciona.  
  
 Una aplicación puede utilizar el estilo de `TBS_AUTOTICKS` para tener marcas de paso de un control deslizante mostradas automáticamente.  Si una aplicación necesita controlar la posición o frecuencia de las marcas de paso, sin embargo, varias funciones miembro pueden utilizar.  
  
 Para establecer la posición de una marca de graduación, una aplicación puede utilizar la función miembro de [SetTic](../Topic/CSliderCtrl::SetTic.md) .  La función miembro de [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md) permite a una aplicación establecer las marcas de graduación que aparecen a intervalos regulares en el intervalo de control slider.  Por ejemplo, la aplicación puede utilizar esta función miembro para mostrar solo 10 marcas de paso en un intervalo de 1 a 100.  
  
 Para recuperar el índice del intervalo correspondiente a una marca de graduación, utilice la función miembro de [GetTic](../Topic/CSliderCtrl::GetTic.md) .  La función miembro de [GetTicArray](../Topic/CSliderCtrl::GetTicArray.md) recupera una matriz de estos índices.  Para recuperar la posición de una marca de graduación, en coordenadas de cliente, utilice la función miembro de [GetTicPos](../Topic/CSliderCtrl::GetTicPos.md) .  Una aplicación puede recuperar el número de marcas de paso utilizando la función miembro de [GetNumTics](../Topic/CSliderCtrl::GetNumTics.md) .  
  
 La función miembro de [ClearTics](../Topic/CSliderCtrl::ClearTics.md) quita todas las marcas de paso de un control deslizante.  
  
 Un tamaño de la línea de control deslizante determina hasta qué punto los movimientos de control deslizante cuando una aplicación recibe un mensaje de notificación de **TB\_LINEDOWN** o de **TB\_LINEUP** .  De igual forma, el tamaño de página determina la respuesta a los mensajes de notificación de **TB\_PAGEDOWN** y de **TB\_PAGEUP** .  Las aplicaciones pueden recuperar y establecer los valores de línea y el tamaño de página mediante [GetLineSize](../Topic/CSliderCtrl::GetLineSize.md), [SetLineSize](../Topic/CSliderCtrl::SetLineSize.md), [GetPageSize](../Topic/CSliderCtrl::GetPageSize.md), y el miembro de [SetPageSize](../Topic/CSliderCtrl::SetPageSize.md) funciona.  
  
 Una aplicación puede utilizar funciones miembro para recuperar las dimensiones de un control deslizante.  La función miembro de [GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md) recupera el rectángulo delimitador para el control deslizante.  La función miembro de [GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md) recupera el rectángulo delimitador para el canal de control slider. \(El canal de El es el área en la que el control deslizante desplaza y la que contiene el resaltado cuando se selecciona un intervalo\).  
  
 Si un control deslizante tiene el estilo de `TBS_ENABLESELRANGE` , el usuario puede seleccionar un intervalo de valores contiguos de.  Varias funciones miembro permiten que el intervalo de selección está ajustado dinámicamente.  La función miembro de [SetSelection](../Topic/CSliderCtrl::SetSelection.md) establece las posiciones inicial y final de una selección.  Cuando el usuario ha terminado de establecer un intervalo de selección, una aplicación puede recuperar la configuración utilizando la función miembro de [GetSelection](../Topic/CSliderCtrl::GetSelection.md) .  Para borrar la selección de un usuario, utilice la función miembro de [ClearSel](../Topic/CSliderCtrl::ClearSel.md) .  
  
## Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)