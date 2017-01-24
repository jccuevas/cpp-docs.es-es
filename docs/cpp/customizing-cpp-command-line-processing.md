---
title: "Personalizar el procesamiento de l&#237;nea de comandos de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setenvp"
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv (función)"
  - "_setenvp (función)"
  - "línea de comandos, procesar"
  - "línea de comandos, procesar argumentos"
  - "procesamiento de línea de comandos"
  - "entorno, rutina de procesamiento de entorno"
  - "código de inicio, personalizar el procesamiento de línea de comandos"
  - "suprimir el procesamiento de entorno"
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Personalizar el procesamiento de l&#237;nea de comandos de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Si el programa no acepta argumentos de línea de comandos, puede guardar una pequeña cantidad de espacio suprimiendo el uso de la rutina de biblioteca que realiza el procesamiento de la línea de comandos.  Esta rutina se denomina **\_setargv** y se describe en [Expansión de caracteres comodín](../cpp/wildcard-expansion.md).  Para suprimir su uso, defina una rutina que no haga nada en el archivo que contiene la función **main** y denomínela **\_setargv**.  La llamada a **\_setargv** se satisface entonces mediante la definición de **\_setargv** y la versión de la biblioteca no se carga.  
  
 De igual forma, si nunca tiene acceso a la tabla de entorno mediante el argumento `envp`, puede proporcionar una rutina vacía propia que se utilizará en lugar de **\_setenvp**, la rutina de procesamiento de entorno.  Igual que con la función de **\_setargv**, **\_setenvp** se debe declarar como **extern "C"**.  
  
 El programa puede realizar llamadas a la familia de rutinas **spawn** o `exec` de la biblioteca en tiempo de ejecución de C.  Si es así, no debe suprimir la rutina de procesamiento de entorno, puesto que esta rutina se utiliza para pasar un entorno del proceso primario al proceso secundario.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [main: inicio de programa](../cpp/main-program-startup.md)