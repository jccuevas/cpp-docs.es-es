---
title: "Estilos de control deslizante | Microsoft Docs"
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
  - "CSliderCtrl (clase), estilos"
  - "controles deslizantes, estilos"
  - "estilos, CSliderCtrl"
  - "estilos, controles deslizantes"
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Estilos de control deslizante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles deslizantes \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) pueden tener una vertical u horizontal.  No pueden tener marcas de paso por dos partes, ambos lados, o ninguno.  También se pueden utilizar para especificar un intervalo de valores consecutivos.  Estas propiedades se controlan mediante los estilos del control deslizante, que se especifican cuando se crea el control deslizante.  
  
 Los estilos de `TBS_HORZ` y de `TBS_VERT` determinan la orientación del control deslizante.  Si no especifica una orientación, el control deslizante se orienta horizontalmente.  
  
 El estilo de `TBS_AUTOTICKS` crea un control deslizante que tiene una marca de graduación para cada incremento en el intervalo de valores.  Estas marcas de paso se agregan automáticamente al llamar a la función miembro de [SetRange](../Topic/CSliderCtrl::SetRange.md) .  Si no especifica `TBS_AUTOTICKS`, puede utilizar funciones miembro, como [SetTic](../Topic/CSliderCtrl::SetTic.md) y [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md), para especificar las posiciones de las marcas de paso.  Para crear un control deslizante controle qué no muestra marcas de paso, puede utilizar el estilo de `TBS_NOTICKS` .  
  
 Puede mostrar marcas de paso de o ambos lados del control deslizante.  Para los controles horizontal de control deslizante, puede especificar el estilo de `TBS_BOTTOM` o de `TBS_TOP` .  Para los controles en paralelo de control deslizante, puede especificar el estilo de `TBS_RIGHT` o de `TBS_LEFT` . \(`TBS_BOTTOM` y `TBS_RIGHT` son los predeterminados.\) Por marcas de paso a ambos lados del control deslizante en cualquier guía, especifique el estilo de `TBS_BOTH` .  
  
 Un control deslizante puede mostrar un intervalo de selección sólo si especifica el estilo de `TBS_ENABLESELRANGE` cuando lo crea.  Cuando un control deslizante tiene este estilo, las marcas de graduación en las posiciones inicial y final de un intervalo de selección se muestran como triángulos \(en lugar de guiones verticales\) y se resalta el intervalo de selección.  Por ejemplo, los intervalos de selección pueden resultar útiles en una aplicación de programación simple.  El usuario podría seleccionar un radio de acción de marcas de paso correspondiente a horas en un día para identificar una hora de la reunión programada.  
  
 De forma predeterminada, el control deslizante de un control deslizante varía con los cambios en el intervalo de selección.  Si el control deslizante tiene el estilo de **TBS\_FIXEDLENGTH** , el control deslizante sigue siendo el mismo incluso si los cambios del intervalo de la selección.  Un control deslizante que tiene el estilo de **TBS\_NOTHUMB** no incluye un control deslizante.  
  
## Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)