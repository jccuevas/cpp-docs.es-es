---
title: "SDI y MDI | Microsoft Docs"
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
  - "ventanas de marco, MDI (aplicaciones)"
  - "ventanas de marco, SDI (aplicaciones)"
  - "MDI, SDI"
  - "MFC, ventanas"
  - "interfaz de único documento (SDI), aplicaciones"
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SDI y MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC facilita trabajar con aplicaciones de \(MDI\) de interfaz de un único documento \(SDI\) y de interfaz de múltiples documentos.  
  
 Las aplicaciones SDI permiten sólo una ventana de marco de documento abierto al mismo tiempo.  Las aplicaciones MDI permiten que varias ventanas de marco de documento se abre en la misma instancia de una aplicación.  Una aplicación MDI tiene una ventana en la que las ventanas secundarias de MDI, que son ventanas propios de marco, pueden ser abiertas, cada uno de los cuales contiene un documento independiente.  En algunas aplicaciones, las ventanas secundarias pueden ser de tipos diferentes, como ventanas de gráfico y ventanas de la hoja de cálculo.  En ese caso, la barra de menús puede cambiar mientras las ventanas secundarias MDI de diferentes tipos se generan.  
  
> [!NOTE]
>  En Windows 95 y versiones posteriores, las aplicaciones son normalmente SDI porque el sistema operativo ha adoptado una vista “documento\- centrada”.  
  
 Para obtener más información, vea [Documentos, vistas, y el marco](../mfc/documents-views-and-the-framework.md).  
  
## Vea también  
 [Usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)