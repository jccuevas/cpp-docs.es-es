---
title: "Sintaxis de la l&#237;nea de comandos del compilador | Microsoft Docs"
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
  - "cl.exe (compilador), sintaxis de línea de comandos"
  - "sintaxis, línea de comandos del compilador CL"
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sintaxis de la l&#237;nea de comandos del compilador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En la línea de comandos de CL se utiliza la siguiente sintaxis:  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 En la tabla siguiente se explican las entradas del comando de CL.  
  
|Entry|Significado|  
|-----------|-----------------|  
|*Opción*|Una o varias [opciones de CL](../../build/reference/compiler-options.md).  Tenga en cuenta que todas las opciones se aplican a todos los archivos de código fuente especificados.  Las opciones se especifican mediante una barra diagonal \(\/\) o un guión \(–\).  Si una opción recibe un argumento, la descripción de la opción documentará si se permite un espacio entre ella y el argumento.  Los nombres de opción \(excepto \/HELP\) hacen distinción entre mayúsculas y minúsculas.  Vea [Orden de las opciones de CL](../../build/reference/order-of-cl-options.md) para obtener más información.|  
|`file`|Nombre de uno o varios archivos de código fuente, archivos .obj o bibliotecas.  CL compila los archivos de código fuente y pasa al vinculador los nombres de los archivos .obj y las bibliotecas.  Vea la [Sintaxis de los nombres de archivo de CL](../../build/reference/cl-filename-syntax.md) para obtener más información.|  
|*lib*|Uno o varios nombres de biblioteca.  CL pasa estos nombres al vinculador.|  
|*command\-file*|Archivo que contiene varios nombres de archivo y opciones.  Vea [Archivos de comandos CL](../../build/reference/cl-command-files.md) para obtener más información.|  
|*link\-opt*|Una o varias [opciones de vinculador](../../build/reference/linker-options.md).  CL pasa estas opciones al vinculador.|  
  
 Es posible especificar cualquier número de opciones, nombres de archivo y nombres de biblioteca, siempre y cuando el número de caracteres de la línea de comandos no supere los 1024, límite dictado por el sistema operativo.  
  
 Para obtener información sobre el valor devuelto de cl.exe, vea [Valor devuelto de cl.exe](../../build/reference/return-value-of-cl-exe.md).  
  
> [!NOTE]
>  No se garantiza que en futuras versiones de Windows se conserve el límite de 1024 caracteres de entrada en la línea de comandos.  
  
## Vea también  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)