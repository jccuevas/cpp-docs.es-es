---
title: "Error del compilador C3505 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3505"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3505"
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C3505
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede cargar la biblioteca de tipos 'guid  
  
 El error C3505 puede deberse a que se está ejecutando el compilador cruzado de 64 bits \(32 bit\) en un equipo de 64 bits porque el compilador se ejecuta con WOW64 y sólo puede leer el subárbol de 32 bits del Registro.  
  
 Puede resolverlo compilando versiones de 32 bits y de 64 bits de la biblioteca de tipos que intenta importar y registrar ambas.  O puede utilizar el compilador de 64 bits nativo, en cuyo caso deberá cambiar los Directorios de VC\+\+ del IDE para señalar el compilador de 64 bits.  
  
 Para obtener más información, vea  
  
-   [Cómo: Habilitar un conjunto de herramientas de Visual C\+\+ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Cómo: Habilitar un conjunto de herramientas de Visual C\+\+ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Cómo: Configurar proyectos de Visual C\+\+ en plataformas de 64 bits de destino](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)