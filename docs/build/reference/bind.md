---
title: "/BIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/bind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BIND (opción de editbin)"
  - "BIND (opción de editbin)"
  - "-BIND (opción de editbin)"
  - "puntos de entrada"
  - "puntos de entrada, direcciones"
  - "tabla de direcciones de importación"
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /BIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BIND[:PATH=path]  
```  
  
## Comentarios  
 Esta opción establece las direcciones de los puntos de entrada de la tabla de direcciones de importación para un archivo ejecutable o un archivo DLL.  Puede utilizar esta opción para reducir el tiempo de carga de un programa.  
  
 Especifique el archivo ejecutable del programa y los archivos DLL en el argumento *files* de la línea de comandos de EDITBIN.  El argumento opcional *path* de la opción \/BIND especifica la ubicación de los archivos DLL que se utilizan en los archivos especificados.  Debe separar los distintos directorios con puntos y comas \(**;**\).  Si no especifica el valor de *path*, EDITBIN buscará en los directorios especificados en la variable de entorno PATH.  Si especifica el valor de *path*, EDITBIN pasará por alto la variable PATH.  
  
 De manera predeterminada, el cargador del programa establecerá las direcciones de los puntos de entrada cuando cargue un programa.  La cantidad de tiempo que dura este proceso variará en función del número de archivos DLL y del número de puntos de entrada a los que haga referencia el programa.  Si se modificó un programa con la opción \/BIND y no hay ningún conflicto entre las direcciones base del archivo ejecutable y sus DLL, y las DLL que ya están cargadas, el sistema operativo no tendrá que establecer estas direcciones.  Si los archivos tienen una base incorrecta, el sistema operativo volverá a buscar la ubicación de los archivos DLL y a calcular las direcciones de los puntos de entrada, lo que incrementará el tiempo de carga del programa.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)