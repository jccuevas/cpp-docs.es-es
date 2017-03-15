---
title: "Desplazar y escalar vistas | Microsoft Docs"
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
  - "controladores de mensajes"
  - "control de mensajes, barras de desplazamiento en clase de vista"
  - "escalar vistas"
  - "barras de desplazamiento, mensajes"
  - "desplazar vistas"
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Desplazar y escalar vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC admite vistas que se desplazan y vistas que automáticamente se ajusta al tamaño de la ventana de marco que las muestra.  La clase `CScrollView` admite ambos tipos de vistas.  
  
 Para obtener más información sobre el desplazamiento y el ajuste de escala, vea la clase [CScrollView](../mfc/reference/cscrollview-class.md) en *la referencia de MFC*.  Para obtener un ejemplo de desplazamiento, vea [Scribble el ejemplo](../top/visual-cpp-samples.md).  
  
## ¿Sobre qué desea obtener más información?  
  
-   Mover una vista  
  
-   Escalar una vista  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f321fcf7c88bc6e3f892ae0fc9b2f0d8" class\="tgtSentence"\>Coordenadas de vista\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a> Mover una vista  
 Con frecuencia el tamaño de un documento es mayor que el tamaño de la vista puede mostrar.  Esto puede ocurrir porque los datos del documento aumenta o el usuario reduce la ventana esa cuadros la vista.  En estos casos, la vista debe admitir el desplazamiento.  
  
 Cualquier vista puede controlar mensajes de la barra de desplazamiento en la `OnHScroll` y el miembro de `OnVScroll` funciona.  Puede o implementar el control de mensajes de la barra de desplazamiento en estas funciones, haciendo todo el trabajo, o la clase de `CScrollView` para controlar el desplazamiento automáticamente.  
  
 `CScrollView` hace lo siguiente:  
  
-   Administra los tamaños de la ventana y de la ventanilla y los modos de asignación  
  
-   Desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento  
  
 Puede especificar cuántas para desplazarse a una “página” \(cuando el usuario hace clic en un eje de la barra de desplazamiento\) y una “línea” \(cuando el usuario hace clic en una flecha de desplazamiento\).  Planear estos valores para ajustarse a la naturaleza de la vista.  Por ejemplo, es posible que desee mover en incrementos de 1 píxel en una vista de gráficos pero en incrementos según el alto de línea en documentos de texto.  
  
##  <a name="_core_scaling_a_view"></a> Escalar una vista  
 Si desea que la vista automáticamente para ajustarse el tamaño de la ventana de marco, puede utilizar `CScrollView` escalar en lugar de desplazamiento.  La vista lógica se ajusta o se reduce para ajustarse el área cliente de la ventana exactamente.  Una vista escalada no tiene ninguna barra de desplazamiento.  
  
## Vea también  
 [Usar vistas](../mfc/using-views.md)