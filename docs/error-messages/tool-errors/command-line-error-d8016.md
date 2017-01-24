---
title: "Error de la l&#237;nea de comandos D8016 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8016"
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de la l&#237;nea de comandos D8016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las opciones de línea de comandos 'opción1' y 'opción2' son incompatibles  
  
 Las opciones de la línea de comandos no se pueden especificar juntas.  
  
 Compruebe si hay especificaciones de opción en las variables de entorno, como CL.  
  
 **\/clr** implica **\/EHa** y no se puede especificar ninguna otra opción del compilador **\/EH** con **\/clr**.  Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 El error D8016 puede aparecer después de actualizar un proyecto de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0: el proceso del asistente para la actualización de proyectos puede habilitar la opción **\/RTC** para cada archivo de código fuente del proyecto, lo que invalida el valor de **\/RTC** para el proyecto.  Para solucionarlo, cambie el valor de **\/RTC** al valor predeterminado para cada archivo de código fuente del proyecto; esto significa que el valor de **\/RTC**  para el proyecto es extensible a cada archivo.  
  
 Vea [\/RTC \(Comprobaciones de errores en tiempo de ejecución\)](../../build/reference/rtc-run-time-error-checks.md) para obtener información sobre cómo cambiar el valor de la propiedad **\/RTC**.