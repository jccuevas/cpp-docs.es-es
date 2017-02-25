---
title: "Personalizar el procesamiento de l&#237;nea de comandos de C | Microsoft Docs"
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
  - "_exec (función)"
  - "_setargv (función)"
  - "_spawn (funciones)"
  - "línea de comandos, procesar"
  - "línea de comandos, procesar argumentos"
  - "procesamiento de línea de comandos"
  - "entorno, rutina de procesamiento de entorno"
  - "código de inicio, personalizar el procesamiento de línea de comandos"
  - "suprimir el procesamiento de entorno"
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Personalizar el procesamiento de l&#237;nea de comandos de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el programa no acepta argumentos de línea de comandos, puede guardar una pequeña cantidad de espacio suprimiendo el uso de la rutina de biblioteca que realiza el procesamiento de la línea de comandos.  Esta rutina se denomina **\_setargv** \(o **\_wsetargv** en el entorno de caracteres anchos\), como se describe en [Expansión de argumentos comodín](../c-language/expanding-wildcard-arguments.md).  Para suprimir su uso, defina una rutina que no haga nada en el archivo que contiene la función **main** y denomínela **\_setargv** \(o **\_wsetargv** en el entorno de caracteres anchos\).  La llamada a **\_setargv** o **\_wsetargv** se satisface mediante la definición de **\_setargv** o **\_wsetargv** y no se carga la versión de la biblioteca.  
  
 De igual forma, si nunca tiene acceso a la tabla de entorno mediante el argumento `envp`, puede proporcionar una rutina vacía propia que se utilizará en lugar de **\_setenvp** \(o **\_wsetenvp**\), la rutina de procesamiento de entorno.  
  
 Si el programa realiza llamadas a la familia de rutinas **\_spawn** o **\_exec** de la biblioteca en tiempo de ejecución de C, no debe suprimir la rutina de procesamiento de entorno, puesto que esta rutina se utiliza para pasar un entorno desde el proceso de generación al nuevo proceso.  
  
## Vea también  
 [Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)