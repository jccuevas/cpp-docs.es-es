---
title: "Archivos de comandos de CL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), archivos de comandos"
  - "archivos de comandos"
  - "archivos de comandos, compilador CL"
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos de comandos de CL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un archivo de comandos es un archivo de texto que contiene opciones y nombres de archivo que, en otras circunstancias, se escribirían en la [línea de comandos](../../build/reference/compiler-command-line-syntax.md) o se especificarían por medio de la [variable de entorno CL](../../build/reference/cl-environment-variables.md).  CL acepta los archivos de comandos del compilador como argumentos de la variable de entorno CL o de la línea de comandos.  A diferencia de la línea de comandos o la variable de entorno CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.  
  
 Las opciones y los nombres de archivo de un archivo de comandos se procesan conforme a la ubicación del archivo de comandos dentro de la variable de entorno CL o de la línea de comandos.  Sin embargo, si se incluye la opción \/link en el archivo de comandos, todas las opciones del resto de la línea pasarán al vinculador.  Las opciones de las siguientes líneas del archivo de comandos y las opciones de la línea de comandos que sean posteriores a la llamada al archivo de comandos seguirán aceptándose como opciones del compilador.  Para obtener más información sobre cómo afecta el orden de las opciones a su interpretación, vea [Orden de las opciones de CL](../../build/reference/order-of-cl-options.md).  
  
 Un archivo de comandos no puede contener el comando de CL.  Las opciones deben empezar y terminar en la misma línea; no puede utilizarse la barra diagonal inversa \(\\\) para combinar una opción en dos líneas.  
  
 Un archivo de comandos se especifica mediante el signo arroba \(@\) seguido de un nombre de archivo; el nombre de archivo puede especificar una ruta de acceso absoluta o relativa.  
  
 Por ejemplo, si el siguiente comando se encuentra en un archivo denominado RESP:  
  
```  
/Og /link LIBC.LIB  
```  
  
 y se especifica el siguiente comando de CL:  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 CL recibirá el siguiente comando:  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 Observe que los comandos de la línea de comandos y del archivo de comandos se han combinado con éxito.  
  
## Vea también  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)