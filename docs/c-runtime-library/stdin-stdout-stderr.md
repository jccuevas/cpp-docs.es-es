---
title: stdin, stdout, stderr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f6226a6e38326a39ce2921e2a0d6219d01f005b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr
## <a name="syntax"></a>Sintaxis  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Se trata de las secuencias estándar de entrada, salida y salida de errores.  
  
 De forma predeterminada, la entrada estándar se lee desde el teclado, mientras que la salida estándar y el error estándar se imprimen en la pantalla.  
  
 Los siguientes punteros de secuencia están disponibles para acceder a las secuencias estándar:  
  
|Puntero|Secuencia|  
|-------------|------------|  
|`stdin`|Entrada estándar|  
|**stdout**|Salida estándar|  
|`stderr`|Error estándar|  
  
 Estos punteros pueden usarse como argumentos para las funciones. Algunas funciones, como **getchar** y `putchar`, use `stdin` y **stdout** automáticamente.  
  
 Estos punteros son constantes, y no se pueden asignar nuevos valores. La función `freopen` puede usarse para redirigir las secuencias a archivos de disco o a otros dispositivos. El sistema operativo permite redirigir una entrada y salida estándar del programa a nivel de comando.  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)