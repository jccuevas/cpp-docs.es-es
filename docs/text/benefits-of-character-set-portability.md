---
title: "Ventajas de la portabilidad de los juegos de caracteres | Microsoft Docs"
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
  - "juegos de caracteres [C++], ventajas"
  - "portabilidad [C++], juegos de caracteres"
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Ventajas de la portabilidad de los juegos de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es posible aprovecharse de la utilización de las características de portabilidad en tiempo de ejecución de C y MFC aun en el caso de que no se desee internacionalizar la aplicación actualmente:  
  
-   La creación de código portable flexibiliza la base del código.  Más tarde se puede pasar fácilmente a Unicode o a MBCS.  
  
-   La utilización de Unicode aumenta la eficacia de las aplicaciones para Windows 2000.  Windows 2000 utiliza Unicode, por lo que las cadenas que no son de Unicode enviadas al sistema operativo o transferidas desde el mismo deben convertirse, provocándose una sobrecarga.  
  
-   La utilización de MBCS permite la compatibilidad con los mercados internacionales en plataformas Win32 distintas de Windows 2000, como Windows 95 o Windows 98.  
  
## Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Compatibilidad con Unicode](../text/support-for-unicode.md)