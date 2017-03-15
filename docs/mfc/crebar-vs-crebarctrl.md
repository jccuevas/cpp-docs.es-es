---
title: "CReBar frente a CReBarCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CReBar"
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar (clase), frente a CReBarCtrl"
  - "GetReBarCtrl (clase)"
  - "controles rebar, CReBarCtrl (clase)"
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReBar frente a CReBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona dos clases para crear rebars: [CReBar](../mfc/reference/crebar-class.md) y [CReBarCtrl](../mfc/reference/crebarctrl-class.md) \(que contiene el control común API de Windows\).  **CReBar** proporciona toda la funcionalidad del control común rebar, y controla muchos de los valores necesarios y estructuras de control común para usted.  
  
 `CReBarCtrl` es una clase contenedora para el control rebar de Win32, por lo que puede ser más fácil de implementar si no piensa integrar el rebar en la arquitectura de MFC.  Si piensa utilizar `CReBarCtrl` y para integrar el rebar en la arquitectura de MFC, debe tener cuidado adicional para comunicar manipulaciones de control rebar a MFC.  Esta comunicación no es difícil; sin embargo, es el trabajo adicional que no es necesario cuando se utiliza **CReBar**.  
  
 Visual C\+\+ proporciona dos maneras de aprovechar el control común rebar.  
  
-   Cree el rebar mediante **CReBar**, y llame a [CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md) para obtener acceso a las funciones miembro de `CReBarCtrl` .  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` es una función inline miembro que convierte el puntero de **this** de objeto rebar.  Esto significa que, en tiempo de ejecución, la llamada de función no tiene ninguna sobrecarga.  
  
-   Cree el rebar utilizando el constructor de [CReBarCtrl](../mfc/reference/crebarctrl-class.md) .  
  
 Cualquier método dará el acceso a las funciones miembro de control rebar.  Cuando se llama a `CReBar::GetReBarCtrl`, devuelve una referencia a un objeto de `CReBarCtrl` para poder utilizar alguna establece de funciones miembro.  Vea [CReBar](../mfc/reference/crebar-class.md) para obtener información sobre la construcción y crear un rebar mediante **CReBar**.  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)