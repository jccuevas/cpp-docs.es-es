---
title: "Constantes de modo de traducción | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs: C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f5224064158dcbcb277524af21a0059a324fbc5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="translation-mode-constants"></a>Constantes del modo de traducción
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las constantes del manifiesto `_O_BINARY` y `_O_TEXT` determinan el modo de traducción de archivos (`_open` y `_sopen`) o el modo de traducción de secuencias (`_setmode`).  
  
 Los valores permitidos son:  
  
 `_O_TEXT`  
 Abre un archivo en modo de texto (traducido). Las combinaciones de retorno de carro y avance de línea (CR-LF) se traducen en un único carácter de avance de línea (LF) en la entrada. Los caracteres de salto de línea se traducen en combinaciones CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura y lectura y escritura, `fopen` comprueba si existe un CTRL+Z al final del archivo y lo quita, si es posible. Se hace así porque el uso de las funciones `fseek` y `ftell` para desplazarse por un archivo que finaliza con CTRL+Z puede hacer que `fseek` se comporte de manera incorrecta cerca del final del archivo.  
  
 `_O_BINARY`  
 Abre un archivo en modo binario (sin traducir). Las traducciones anteriores se suprimen.  
  
 `_O_RAW`  
 Igual a `_O_BINARY`. Admite la compatibilidad con C 2.0.  
  
 Para obtener más información, vea [E/S de archivo en modo texto y en modo binario](../c-runtime-library/text-and-binary-mode-file-i-o.md) y [Constantes de traducción de archivo](../c-runtime-library/file-translation-constants.md).  
  
## <a name="see-also"></a>Vea también  
 [_open, _wopen](../c-runtime-library/reference/open-wopen.md)   
 [_pipe](../c-runtime-library/reference/pipe.md)   
 [_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode](../c-runtime-library/reference/setmode.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)