---
title: "Establecer las opciones del vinculador | Microsoft Docs"
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
  - "archivos [C++], LINK"
  - "archivos de entrada [C++]"
  - "archivos de entrada [C++], vinculador"
  - "vinculador [C++], modificadores"
  - "vinculador [C++], maneras de establecer opciones"
  - "módulos de objetos/bibliotecas"
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Establecer las opciones del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las opciones del vinculador pueden establecerse tanto dentro como fuera del entorno de desarrollo.  En el tema correspondiente a cada opción del vinculador se explica cómo deben establecerse éstas en el entorno de desarrollo.  Para obtener una lista completa, vea [Opciones del vinculador](../../build/reference/linker-options.md).  
  
 Si LINK se va a ejecutar fuera del entorno de desarrollo, es posible especificar la entrada de varias formas:  
  
-   En la [línea de comandos](../../build/reference/linker-command-line-syntax.md)  
  
-   Mediante [archivos de comandos](../../build/reference/link-command-files.md) &#124;  
  
-   En [variables de entorno](../../build/reference/link-environment-variables.md)  
  
 LINK procesa en primer lugar las opciones especificadas en la variable de entorno LINK, y, después, las restantes opciones, en el orden en que estén especificadas en la línea de comandos y en los archivos de comandos.  Si una opción se repite con argumentos distintos, tendrá precedencia la que se procese en último lugar.  
  
 Las opciones se aplican a toda la compilación: no pueden aplicarse a archivos de entrada individuales.  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)