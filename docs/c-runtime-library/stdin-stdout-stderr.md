---
title: stdin, stdout, stderr | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
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
ms.openlocfilehash: 707811a9c05135cb46520dd72895d677cdc0a6e4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808711"
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
|`stdout`|Salida estándar|
|`stderr`|Error estándar|

Estos punteros pueden usarse como argumentos para las funciones. Algunas funciones, como [getchar](../c-runtime-library/reference/getchar-getwchar.md) y [putchar](../c-runtime-library/reference/putchar-putwchar.md), usan `stdin` y `stdout` automáticamente.

Estos punteros son constantes, y no se pueden asignar nuevos valores. La función [freopen](../c-runtime-library/reference/freopen-wfreopen.md) puede usarse para redirigir las secuencias a archivos de disco o a otros dispositivos. El sistema operativo permite redirigir una entrada y salida estándar del programa a nivel de comando.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../c-runtime-library/stream-i-o.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
