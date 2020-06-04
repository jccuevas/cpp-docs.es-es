---
title: Estados de secuencia
ms.date: 11/19/2018
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
ms.openlocfilehash: f725fa16e8d669975dbc02c6eefd727085bbeb7c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743353"
---
# <a name="stream-states"></a>Estados de secuencia

En la siguiente ilustración se muestran los estados válidos y las transiciones de estado de una secuencia.

![Diagrama de estado de secuencia](../c-runtime-library/media/stream.gif "Stream state diagram")

Cada uno de los círculos indica un estado estable. Cada una de las líneas indica una transición que se puede producir como resultado de una llamada de función que opera en la secuencia. Hay cinco grupos de funciones que pueden provocar transiciones de estado.

Las funciones de los tres primeros grupos se declaran en \<stdio.h >:

- Las funciones de lectura de bytes: [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread](../c-runtime-library/reference/fread.md), [fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [getchar](../c-runtime-library/reference/getc-getwc.md), [gets](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) y [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)

- Las funciones de escritura de bytes: [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs](../c-runtime-library/reference/fputs-fputws.md), [fwrite](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [coloca](../c-runtime-library/reference/puts-putws.md), [vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) y [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- Las funciones de posición: [fflush](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md) y [rebobinar](../c-runtime-library/reference/rewind.md)

Las funciones de los dos grupos restantes se declaran en \<wchar.h >:

- Las funciones de lectura extendida: [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc](../c-runtime-library/reference/getc-getwc.md), [getwchar](../c-runtime-library/reference/getc-getwc.md), [ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md) y [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),

- Las funciones de escritura extendida: [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc](../c-runtime-library/reference/fputc-fputwc.md), [fputws](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) y [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),

El diagrama de estado muestra que debe llamar a una de las funciones de posición entre la mayoría de las operaciones de lectura y escritura:

- No puede llamar a una función de lectura si la última operación del flujo es una operación de escritura.

- No puede llamar a una función de escritura si la última operación del flujo es una operación de lectura, a menos que la operación de lectura establezca el indicador de fin de archivo.

Por último, el diagrama de estado muestra que una operación de posición nunca disminuye el número de llamadas de función válidas que le pueden seguir.

## <a name="see-also"></a>Vea también

[Archivos y secuencias](../c-runtime-library/files-and-streams.md)
