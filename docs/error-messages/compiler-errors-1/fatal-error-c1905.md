---
title: "Error irrecuperable C1905 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1905"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1905"
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error irrecuperable C1905
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Front\-end y back\-end no compatibles \(el destino debe ser el mismo procesador\).  
  
 Este error se produce cuando el front\-end de un compilador \(C1.dll\) cuyo destino es un procesador, por ejemplo x86, ARM o [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] genera un archivo .obj, pero este lo lee un back\-end \(C2.dll\) destinado a un procesador diferente.  
  
 Para resolver este problema, asegúrese de que el front\-end y el back\-end utilizados se corresponden.  Este es el valor predeterminado para los proyectos creados en Visual Studio.  Este error puede producirse si ha editado el archivo de proyecto y si ha utilizado diferentes rutas de acceso a las herramientas del compilador.  Si no ha establecido específicamente la ruta de acceso de las herramientas del compilador, este error puede producirse si la instalación de Visual Studio está dañada.  Por ejemplo, tal vez ha copiado los archivos .dll del compilador de una ubicación a otra.  Utilice **Programas y características** del Panel de control de Windows para reparar o reinstalar Visual Studio.