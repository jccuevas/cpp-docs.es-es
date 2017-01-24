---
title: "Puntos de entrada de procedimiento de ventana | Microsoft Docs"
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
  - "puntos de entrada, procedimientos de ventana"
  - "MFC, administrar datos de estado"
  - "administración de estados, procedimientos de ventana"
  - "puntos de entrada de procedimiento de ventana"
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Puntos de entrada de procedimiento de ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para proteger los procedimientos de ventana de MFC, vínculos de estático de módulo con una aplicación especial de procedimiento de ventana.  La vinculación se produce automáticamente cuando el módulo se vinculan con MFC.  Este procedimiento de ventana utiliza la macro de `AFX_MANAGE_STATE` para establecer correctamente el estado real del módulo, llamar **AfxWndProc**, que a su vez delega a la función de `CWnd`adecuado \(objeto derivado del miembro de `WindowProc` .  
  
## Vea también  
 [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)