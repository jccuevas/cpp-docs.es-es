---
title: "@ (Especificar un archivo de respuesta del compilador) | Microsoft Docs"
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
  - "@"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@ (opción del compilador)"
  - "cl.exe (compilador), especificar archivos de respuesta"
  - "archivos de respuesta, compilador de C/C++"
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @ (Especificar un archivo de respuesta del compilador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un archivo de respuesta del compilador.  
  
## Sintaxis  
  
```  
@response_file  
```  
  
## Argumentos  
 `response_file`  
 Archivo de texto que contiene comandos del compilador.  
  
## Comentarios  
 Un archivo de respuesta puede contener cualquier comando que pueda especificarse en la línea de comandos.  Esto puede ser útil si los argumentos de la línea de comandos superen los 127 caracteres.  
  
 No puede especificarse la opción **@** desde un archivo de respuesta.  Es decir, un archivo de respuesta no puede contener a otro archivo de respuesta.  
  
 Desde la línea de comandos puede especificar tantas opciones de archivo de respuesta como desee \(por ejemplo, `@respfile.1 @respfile.2`\).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
-   Un archivo de respuesta no puede especificarse desde el entorno de desarrollo, sino que debe especificarse en la línea de comandos.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Esta opción del compilador no se puede modificar mediante programación.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)