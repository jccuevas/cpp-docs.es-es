---
title: "Expandir argumentos de caracteres comod&#237;n | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "asterisco (comodín)"
  - "expandir argumentos de caracteres comodín"
  - "signo de interrogación, carácter comodín"
  - "comodines, expandir"
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Expandir argumentos de caracteres comod&#237;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Cuando se ejecuta un programa de C, se puede usar cualquiera de estos dos caracteres comodín —el signo de interrogación \(?\) y el asterisco \(\*\)— para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 De forma predeterminada, los caracteres comodín no se expanden en argumentos de línea de comandos. Puede reemplazar la rutina de carga `argv` del vector de argumento normal por una versión que expanda los caracteres comodín mediante la vinculación con el archivo setargv.obj o wsetargv.obj. Si el programa usa una función `main`, debe vincularse con setargv.obj. Si el programa usa una función `wmain`, debe vincularse con wsetargv.obj. Ambos tienen un comportamiento equivalente.  
  
 Para establecer la vinculación con setargv.obj o wsetargv.obj, use la opción **\/link**. Por ejemplo:  
  
 **cl example.c \/link setargv.obj**  
  
 Los caracteres comodín se expanden de la misma manera que los comandos del sistema operativo. \(Vea la guía del usuario del sistema operativo si no está familiarizado con los caracteres comodín\).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Opciones de vínculo](../c-runtime-library/link-options.md)   
 [Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)