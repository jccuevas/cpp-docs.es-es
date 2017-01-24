---
title: "Relaci&#243;n con la API del lenguaje C | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "libros [C++]"
  - "libros [C++], acerca de MFC y Windows SDK"
  - "MFC [C++], API de Windows"
  - "Visual C, llamadas API de Windows"
  - "API de Windows [C++], y MFC"
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relaci&#243;n con la API del lenguaje C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La única característica que establece la biblioteca de \(MFC\) de la clase de la Microsoft foundation class aparte de otras bibliotecas de clases para Windows es la asignación muy próxima a la API de Windows escrita en el lenguaje C.  Además, puede mezclar normalmente llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows.  Este acceso directo, sin embargo, no significa que las clases son un reemplazo completo para ese API.  Los desarrolladores deben sin embargo hacer ocasionalmente llamadas directas a algunas funciones de Windows, como [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) y [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), por ejemplo.  Una función de Windows es ajustada por una función miembro de clase sólo cuando hay una ventaja clara para ello.  
  
 Dado que a veces es necesario hacer llamadas a funciones nativas de Windows, debe tener acceso a la documentación de API de Windows del lenguaje C.  Esta documentación se incluye con Microsoft Visual C\+\+.  
  
> [!NOTE]
>  Para obtener información general sobre cómo el marco de la biblioteca MFC funciona, vea [Utilizar las clases para escribir las aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## Vea también  
 [Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)