---
title: "stdin, stdout, stderr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdin"
  - "stderr"
  - "stdout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "secuencia de error estándar"
  - "flujo de entrada estándar"
  - "flujo de salida estándar"
  - "stderr (función)"
  - "stdin (función)"
  - "stdout (función)"
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# stdin, stdout, stderr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## Comentarios  
 Éstas son secuencias estándar para la entrada, salida, y la salida de error.  
  
 De forma predeterminada, la entrada estándar se lee del teclado, mientras que imprime a la salida estándar y el error estándar en la pantalla.  
  
 Los punteros de secuencia siguientes están disponibles tener acceso a las secuencias estándar:  
  
|Puntero|Stream|  
|-------------|------------|  
|`stdin`|Entrada estándar|  
|**stdout**|Salida estándar|  
|`stderr`|Error típico|  
  
 Estos punteros se pueden utilizar como argumentos a funciones.  Algo funciona, por ejemplo **getchar** y `putchar`, utilice `stdin` y **stdout** automáticamente.  
  
 Estos punteros son constantes, y no se pueden asignar nuevos valores.  La función de `freopen` se puede utilizar para redirigir secuencias a los archivos de disco u otros dispositivos.  El sistema operativo permite redirigir una norma de programa de entrada y salida en el nivel de comando.  
  
## Vea también  
 [E\/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)