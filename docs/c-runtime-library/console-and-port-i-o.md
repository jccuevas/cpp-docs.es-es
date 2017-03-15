---
title: "E/S de consola y de puerto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "E/S [CRT], consola"
  - "E/S [CRT], puerto"
  - "E/S (rutinas), E/S de consola y puerto"
  - "puertos, E/S (rutinas)"
  - "rutinas"
  - "rutinas, E/S de consola y puerto"
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# E/S de consola y de puerto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Lectura y escritura de estas rutinas en la consola o en el puerto especificado.  Las rutinas de E\/S de consola no son compatibles con E\/S de secuencia o rutinas de biblioteca de E\/S de bajo nivel.  La consola o puerto no tiene que estar abierto o cerrado antes de realizar la E\/S, por lo que no hay rutinas abierto o próximas en esta categoría.  En los sistemas operativos Windows, el resultado de estas funciones se dirige a la consola y no puede ser siempre redirigida.  
  
### Rutinas de E\/S de la consola y de puerto  
  
|Rutina|Utilice|  
|------------|-------------|  
|[\_cgets, \_cgetws](../c-runtime-library/cgets-cgetws.md), [\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Cadena de la consola|  
|[\_cprintf, \_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [\_cprintf\_s, \_cprintf\_s\_l, \_cwprintf\_s, \_cwprintf\_s\_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Datos con formato escribir en la consola|  
|[\_cputs](../c-runtime-library/reference/cputs-cputws.md)|Cadena de escritura a la consola|  
|[\_cscanf, \_cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [\_cscanf\_s, \_cscanf\_s\_l, \_cwscanf\_s, \_cwscanf\_s\_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Datos con formato lectura de consola|  
|[\_getch, \_getwch](../c-runtime-library/reference/getch-getwch.md)|Carácter de la consola|  
|[\_getche, \_getwche](../c-runtime-library/reference/getch-getwch.md)|Carácter de la consola y generación de repetición él|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|Lectura un byte de puerto especificado de E\/S|  
|[\_inpd](../c-runtime-library/inp-inpw-inpd.md)|Doble palabra de lectura de puerto especificado de E\/S|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|Lectura palabra de 2 bytes de puerto especificado de E\/S|  
|[\_kbhit](../c-runtime-library/reference/kbhit.md)|Comprobación de pulsación de tecla en la consola; uso antes de intentar leer desde la consola|  
|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|Escribir un byte al puerto especificado de E\/S|  
|[\_outpd](../c-runtime-library/outp-outpw-outpd.md)|Doble palabra de escritura en el puerto especificado de E\/S|  
|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|Palabra de escritura en el puerto especificado de E\/S|  
|[\_putch, \_putwch](../c-runtime-library/reference/putch-putwch.md)|Carácter de escritura a la consola|  
|[\_ungetch, \_ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|La lectura del último carácter “Unget” de la consola para que de se convierte en lectura el carácter siguiente|  
  
## Vea también  
 [Entrada y salida](../c-runtime-library/input-and-output.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)