---
title: "E/S de secuencias Unicode en los modos binario y de texto | Microsoft Docs"
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
  - "E/S [CRT], secuencia unicode"
  - "rutinas de E/S de secuencia"
  - "E/S de secuencia Unicode"
  - "Unicode, rutinas de E/S de secuencia"
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# E/S de secuencias Unicode en los modos binario y de texto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando una rutina de E\/S de secuencia Unicode \(como `fwprintf`, `fwscanf`, `fgetwc`, `fputwc`, `fgetws`, o `fputws`\) funciona en un archivo que esté abierto en el modo de texto \(valor predeterminado\), dos tipos de conversiones de carácter tienen lugar:  
  
-   Unicode\-a\-MBCS o conversión de MBCS\-a\-Unicode.  Cuando una función de E\/S de secuencia Unicode funciona en modo de texto, la secuencia de origen o de destino se supone que es una secuencia de caracteres multibyte.  Por consiguiente, las funciones de entrada y flujo de Unicode convierten los caracteres multibyte en caracteres anchos \(como si por una llamada a la función de `mbtowc`\).  Por la misma razón, las funciones de salida y flujo Unicode convierten los caracteres anchos en caracteres multibyte \(como si se realizara una llamada a la función de `wctomb`\).  
  
-   Retorno de carro – traducción de avance de línea \(CR\-LF\).  Esta conversión se produce antes de MBCS – conversión Unicode \(para Unicode transmitir funciones de entrada\) y después de Unicode – conversión MBCS \(para Unicode transmitir funciones de resultados\).  Durante entrada, cada retorno de carro \(la combinación de avance de línea se convierte a un único carácter de avance de línea.  Durante salida, cada carácter de avance de línea se convierte a un retorno de carro \(combinación de avance de línea.  
  
 Sin embargo, cuando una función de E\/S de secuencia Unicode funciona en modo binario, el archivo se supone que es Unicode, y ninguna conversión de traducción o de carácter de CR\-LF durante entrada o salida.  Utilice el \_setmode \(\_fileno \(stdin\), \_O\_BINARY\); instrucción para correctamente utilizar wcin en un archivo de texto Unicode.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Entrada y salida](../c-runtime-library/input-and-output.md)