---
title: "Arrastrar y colocar archivos en una ventana de marco | Microsoft Docs"
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
  - "arrastrar y colocar [C++], administrador de archivos"
  - "arrastrar y colocar [C++], archivos"
  - "arrastrar y colocar [C++], Explorador de Windows"
  - "compatibilidad con arrastrar y colocar el Administrador de archivos"
  - "archivos [C++], arrastrar y colocar"
  - "ventanas de marco [C++], arrastrar y colocar archivos en"
  - "Explorador de Windows [C++]"
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arrastrar y colocar archivos en una ventana de marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ventana de marco administra una relación con el Explorador o el administrador de archivos del archivo.  
  
 Agregar algunas llamadas que se inicializan en el reemplazo de la función `InitInstance`miembro de `CWinApp` , como se describe en [CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md), puede tener abrir archivos desde el archivo Explorador o administrador de archivos arrastrado desde la ventana cuadro indirectamente y dividirá en la ventana de marco.  Vea [Arrastrar y colocar del administrador de archivos](../mfc/special-cwinapp-services.md).  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)