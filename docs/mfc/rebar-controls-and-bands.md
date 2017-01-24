---
title: "Controles y bandas Rebar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "bandas, en controles rebar"
  - "controles rebar, trabajar con bandas en"
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles y bandas Rebar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El propósito principal de un control rebar es actuar como contenedor para ventanas secundarias, controles comunes de diálogo, menús, barras de herramientas, etc.  Esta contención admitida por el concepto de una “banda.” Cada banda rebar puede contener cualquier combinación de una barra de agarrador, un mapa de bits, de una etiqueta de texto, y una ventana secundaria.  
  
 La clase `CReBarCtrl` tiene muchas funciones miembro que puede utilizar para recuperar, y manipular, información para una banda específica del rebar:  
  
-   [GetBandCount](../Topic/CReBarCtrl::GetBandCount.md) recupera el número de bandas actuales en el control rebar.  
  
-   [GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md) inicializa una estructura de **REBARBANDINFO** con información de banda especificada.  Hay una función miembro correspondiente de [SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md) .  
  
-   [GetRect](../Topic/CReBarCtrl::GetRect.md) recupera el rectángulo delimitador de una banda especificada.  
  
-   [GetRowCount](../Topic/CReBarCtrl::GetRowCount.md) recupera el número de filas de la banda en un control rebar.  
  
-   [IDToIndex](../Topic/CReBarCtrl::IDToIndex.md) recupera el índice de una banda especificada.  
  
-   [GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md) recupera los bordes de una banda.  
  
 Además de manipulación, varias funciones miembro son que permitan que se opera en bandas específicas rebar.  
  
 [InsertBand](../Topic/CReBarCtrl::InsertBand.md) y [DeleteBand](../Topic/CReBarCtrl::DeleteBand.md) agregan y quitan bandas rebar.  [MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md) y [MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md) afectan al tamaño actual de una banda concreta rebar.  [MoveBand](../Topic/CReBarCtrl::MoveBand.md) cambia el índice de una banda concreta rebar.  [ShowBand](../Topic/CReBarCtrl::ShowBand.md) muestra u oculta una banda rebar de usuario.  
  
 El ejemplo siguiente muestra cómo agregar una banda de la barra de herramientas \(`m_wndToolBar`\) a un control existente rebar \(`m_wndReBar`\).  Banda se describe inicializando la estructura de `rbi` y después llamar a la función miembro de `InsertBand` :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/CPP/rebar-controls-and-bands_1.cpp)]  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)