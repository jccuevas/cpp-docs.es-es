---
title: "Error de las herramientas del vinculador LNK1277 | Microsoft Docs"
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
  - "LNK1277"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1277"
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1277
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró el registro de objeto en pgd \(nombre de archivo\)  
  
 Al utilizar [\/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), la ruta de acceso de uno de los archivos de entrada .lib, def u .obj files era distinta de aquella en la que se encontraban durante \/LTCG:PGINSTRUMENT.  Esto podría deberse a un cambio en la variable de entorno LIB después de \/LTCG:PGINSTRUMENT.  La ruta de acceso completa a los archivos de entrada se almacena en el archivo .pgd.  
  
 \/LTCG:PGOPTIMIZE requiere que las entradas sean idénticas a la fase \/LTCG:PGINSTRUMENT.  
  
 Para solucionar esta advertencia, realice una de las acciones siguientes:  
  
-   Ejecute \/LTCG:PGINSTRUMENT, rehaga todas las ejecuciones de prueba y ejecute \/LTCG:PGOPTIMIZE.  
  
-   Cambie la variable de entorno LIB por lo que era cuando se ejecutó \/LTCG:PGINSTRUMENT.  
  
 No se recomienda tratar de resolver el error LNK1277 utilizando \/LTCG:PGUPDATE.