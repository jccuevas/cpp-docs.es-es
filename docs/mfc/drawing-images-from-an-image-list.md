---
title: "Dibujar im&#225;genes a partir de una lista de im&#225;genes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList (clase), dibujar imágenes desde"
  - "dibujar, imágenes de las listas de imágenes"
  - "listas de imágenes [C++], dibujar imágenes desde"
  - "imágenes [C++], dibujar"
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dibujar im&#225;genes a partir de una lista de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para dibujar una imagen, use la función miembro de [CImageList::Draw](../Topic/CImageList::Draw.md) .  Especificará un puntero a un objeto de contexto del dispositivo, el índice de la imagen para dibujar, la ubicación en el contexto del dispositivo en el que se va a dibujar la imagen, y un conjunto de indicadores para indicar el estilo del gráfico.  
  
 Cuando especifica el estilo de `ILD_TRANSPARENT` , **Dibujar** utiliza un proceso de dos pasos para dibujar una imagen enmascarada.  Primero, realiza una operación lógica \- AND en fragmentos de la imagen y los bits de la máscara.  Realiza una operación de lógico\- XOR en los resultados de la primera operación y los bits del fondo del contexto del dispositivo de destino.  Este proceso crea áreas transparente en la imagen resultante; es decir, cada bit blanco en la máscara hace el bit correspondiente de la imagen resultante sea transparente.  
  
 Antes de mostrar una imagen enmascarada sobre un fondo de color sólido, debe utilizar la función miembro de [SetBkColor](../Topic/CImageList::SetBkColor.md) para establecer el color de fondo de la imagen que aparece al mismo color que el destino.  Establecer el color elimina la necesidad de crear áreas transparente en la imagen y permite a **Dibujar** para copiar la imagen al contexto del dispositivo de destino, lo que da como resultado un aumento significativo en el rendimiento.  Para dibujar la imagen, especifique el estilo de `ILD_NORMAL` cuando se llama a **Dibujar**.  
  
 Puede establecer el color de fondo para una imagen enmascarada lista \([CImageList](../mfc/reference/cimagelist-class.md)\) en cualquier momento de modo que dibuja correctamente en cualquier fondo sólido.  Establecer el color de fondo a `CLR_NONE` hace que las imágenes que se va a dibujar transparente predeterminadamente.  Para recuperar el color de fondo de una imagen, use la función miembro de [GetBkColor](../Topic/CImageList::GetBkColor.md) .  
  
 Los estilos de `ILD_BLEND25` y de `ILD_BLEND50` interpolados la imagen con el color de resaltado del sistema.  Estos estilos son útiles si utiliza una imagen enmascarada para representar un objeto que el usuario puede seleccionar.  Por ejemplo, puede utilizar el estilo de `ILD_BLEND50` para dibujar la imagen cuando el usuario lo selecciona.  
  
 Una imagen nonmasked se copia en el contexto del dispositivo de destino mediante la operación de la trama de **SRCCOPY** .  Los colores de la imagen tienen el mismo independientemente del color de fondo del contexto del dispositivo.  Los estilos de dibujo especificados en **Dibujar** también no tienen ningún efecto en la apariencia de una imagen nonmasked.  
  
 Además de la función miembro de dibujo, otra función, [DrawIndirect](../Topic/CImageList::DrawIndirect.md), amplía la capacidad de generar una imagen.  `DrawIndirect` toma, como parámetro, una estructura de [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) .  Esta estructura se puede utilizar para personalizar la representación de la imagen actual, incluidos los códigos de \(ROP\) de la operación de la trama.  Para obtener más información sobre códigos de dispositivo de protección en caso de volcamiento, vea [Códigos de operación de la trama](http://msdn.microsoft.com/library/windows/desktop/dd162892) y [Mapas de bits como Pinceles](http://msdn.microsoft.com/library/windows/desktop/dd183378) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)