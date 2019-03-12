---
title: E/S de archivo en modo texto y en modo binario
ms.date: 04/11/2018
f1_keywords:
- c.io
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: 2c875350aedadb55d8f96fb682d6215030be2198
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738586"
---
# <a name="text-and-binary-mode-file-io"></a>E/S de archivo en modo texto y en modo binario

Las operaciones de E/S de archivo tienen lugar en uno de los dos modos de conversión, es decir, *texto* o *binario*, según el modo en que se abre el archivo. Los archivos de datos normalmente se procesan en modo de texto. Para controlar el modo de conversión de archivos, se puede:

- Conservar la configuración predeterminada actual y especificar el modo alternativo solo al abrir los archivos seleccionados.

- Usar la función [_set_fmode](../c-runtime-library/reference/set-fmode.md) para cambiar el modo predeterminado para los archivos que se han abierto recientemente. Usar [_get_fmode](../c-runtime-library/reference/get-fmode.md) para encontrar el modo predeterminado actual. La configuración predeterminada inicial es el modo de texto (**_O_TEXT**).

- Cambiar el modo de conversión predeterminado mediante la configuración de la variable global [_fmode](../c-runtime-library/fmode.md) en el programa. La función **_set_fmode** establece el valor de esta variable, pero también puede establecerse directamente.

Cuando se llama a una función file-open como [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) o [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md), puede invalidar el valor predeterminado actual de **_fmode** si especifica el argumento correspondiente para la función [_set_fmode](../c-runtime-library/reference/set-fmode.md). Las secuencias **stdin**, **stdout** y **stderr** siempre se abren en modo de texto de forma predeterminada; también puede invalidar este comportamiento predeterminado al abrir cualquiera de estos archivos. Use [_setmode](../c-runtime-library/reference/setmode.md) para cambiar el modo de conversión con el descriptor de archivo después de que el archivo está abierto.

## <a name="see-also"></a>Vea también

[Entrada y salida](../c-runtime-library/input-and-output.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
