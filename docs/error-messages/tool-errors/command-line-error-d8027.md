---
title: "Error de la l&#237;nea de comandos D8027 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8027"
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de la l&#237;nea de comandos D8027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede ejecutar 'componente'  
  
 El compilador no puede ejecutar el componente del compilador dado o vinculador.  
  
### Posibles causas del error:  
  
1.  Memoria insuficiente para cargar el componente.  Si NMAKE invocó el compilador, ejecute el compilador fuera del archivo MAKE.  
  
2.  El sistema operativo actual no puede ejecutar el componente.  Asegúrese de que la ruta de acceso señala a los archivos ejecutables adecuados para el sistema operativo.  
  
3.  El componente está dañado.  Vuelva a copiar el componente de los discos de distribución mediante el programa de instalación.  
  
4.  Se ha especificado una opción incorrectamente.  Por ejemplo:  
  
    ```  
    cl /B1 file1.c  
    ```