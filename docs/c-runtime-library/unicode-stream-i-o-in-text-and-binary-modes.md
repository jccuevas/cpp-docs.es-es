---
title: E/S de secuencias Unicode en los modos binario y de texto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76e739ae95788448cc655ca18d32aaf1f8a5c90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>E/S de secuencias Unicode en los modos binario y de texto
Cuando una rutina de E/S de secuencias Unicode (como `fwprintf`, `fwscanf`, `fgetwc`, `fputwc`, `fgetws` o `fputws`) actúa en un archivo que está abierto en modo de texto (valor predeterminado), se producen dos tipos de conversiones de caracteres:  
  
-   Conversión de Unicode a MBCS o de MBCS a Unicode. Cuando una función de E/S de secuencias Unicode actúa en modo de texto (valor predeterminado), se supone que el flujo de origen o de destino es una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada de secuencias Unicode convierten los caracteres multibyte en caracteres anchos (como si por una llamada a la función `mbtowc`). Por la misma razón, las funciones de salida y flujo Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función de `wctomb` ).  
  
-   Traducción de retorno de carro a avance de línea (CR-LF). Esta traducción se produce antes de la conversión de MBCS a Unicode (para funciones de entrada de secuencias Unicode) y después de la conversión de Unicode a MBCS (para funciones de salida de secuencias Unicode). Durante la entrada, cada combinación de retorno de carro y avance de línea se traduce en un único carácter de avance de línea. Durante la salida, cada avance de línea se traduce en una combinación de retorno de carro y avance de línea.  
  
 En cambio, cuando una función de E/S de secuencias Unicode funciona en modo binario, se supone que el archivo es Unicode y no se realiza ninguna conversión de caracteres ni traducción CR-LF durante la entrada o salida. Use la instrucción _setmode( _fileno( stdin ), _O_BINARY ); para usar correctamente wcin en un archivo de texto UNICODE.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Entrada y salida](../c-runtime-library/input-and-output.md)