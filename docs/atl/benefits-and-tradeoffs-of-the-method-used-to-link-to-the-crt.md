---
title: "Benefits and Tradeoffs of the Method Used to Link to the CRT | Microsoft Docs"
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
  - "_ATL_MIN_CRT (macro)"
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Benefits and Tradeoffs of the Method Used to Link to the CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El proyecto se puede vincular con CRT dinámicamente o estáticamente.  La tabla siguiente describe las ventajas y las compensaciones implicados en elegir a qué método utilizar.  
  
|Método|Marcado|Equilibrio|  
|------------|-------------|----------------|  
|Vincular estáticamente a CRT<br /><br /> \(**Biblioteca en tiempo de ejecución** establecido en **Single\-threaded**\)|Archivo DLL de CRT no se requiere en el sistema donde la imagen se ejecutará.|Sobre 25K de código de inicio se agrega a la imagen, aumentará sustancialmente su tamaño.|  
|La vinculación dinámica a CRT<br /><br /> \(**Biblioteca en tiempo de ejecución** establecido en **Multiproceso**\)|La imagen no requiere código de inicio CRT, por lo que es mucho menor.|Archivo DLL de CRT debe estar en el sistema que ejecuta la imagen.|  
  
 El tema [La vinculación a CRT en el proyecto de IU ATL](../atl/linking-to-the-crt-in-your-atl-project.md) describe cómo seleccionar la manera en que vincular a CRT.  
  
## Vea también  
 [Programar con ATL y código en tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Comportamiento de la biblioteca en tiempo de ejecución](../build/run-time-library-behavior.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)