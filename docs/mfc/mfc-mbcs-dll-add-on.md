---
title: "Complemento DLL de MBCS para MFC | Microsoft Docs"
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
  - "MBCS"
  - "MFC"
ms.assetid: bebec0ff-e019-42ca-b5df-8c218ac5b54a
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Complemento DLL de MBCS para MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En Visual Studio 2015, la biblioteca MFC de codificación de caracteres multibyte \(MBCS\) se incluye en los componentes de instalación de Visual C\+\+. Visual C\+\+ y MFC son configuraciones de instalación opcional en el programa de instalación de Visual Studio. Para asegurarse de que MFC está instalado, elija **Personalizado** en el programa de instalación y en **Lenguajes de programación**, asegúrese de que estén seleccionadas las opciones **Visual C\+\+** y **Microsoft Foundation Classes para C\+\+**. Si ya instaló Visual Studio, se le pedirá que instale Visual C\+\+ o MFC cuando intente crear un proyecto MFC.  
  
 Las DLL multibyte son necesarias para compilar un proyecto MFC en Visual Studio 2015 que tenga la propiedad **Juego de caracteres** establecida en **Utilizar juego de caracteres multibyte** o **Sin establecer**.  
  
## Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)