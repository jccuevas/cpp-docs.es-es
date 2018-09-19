---
title: E/S de consola y de puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e0750a2c0b8747da432efd9fc465b83e01a490
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018280"
---
# <a name="console-and-port-io"></a>E/S de consola y de puerto

Estas rutinas leen y escriben en la consola o en el puerto especificado. Las rutinas de E/S de consola no son compatibles con las rutinas de la biblioteca de E/S de secuencia o de E/S de bajo nivel. No es necesario abrir ni cerrar la consola o el puerto antes de ejecutar la E/S, por lo que no hay rutinas abiertas ni cerradas en esta categoría. En los sistemas operativos Windows, el resultado de estas funciones siempre se dirige a la consola y no se puede redirigir.

## <a name="console-and-port-io-routines"></a>Rutinas de E/S de consola y de puerto

|Rutina|Usar|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Leer cadena de la consola|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Escribir datos con formato en la consola|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|Escribir cadena en la consola|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Leer datos con formato de la consola|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Leer carácter de la consola|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Leer carácter de la consola y reproducirlo|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Leer un byte del puerto de E/S especificado|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|Leer doble palabra del puerto de E/S especificado|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Leer palabra de 2 bytes del puerto de E/S especificado|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Buscar pulsación de tecla en la consola; usarla antes de intentar leer de la consola|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|Escribir un byte en el puerto de E/S especificado|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|Escribir doble palabra en el puerto de E/S especificado|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Escribir palabra en el puerto de E/S especificado|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Escribir carácter en la consola|
|[_ungetch, _ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|Aplicar el método "unget" al último carácter leído de la consola, para que sea la siguiente lectura de caracteres|

## <a name="see-also"></a>Vea también

[Entrada y salida](../c-runtime-library/input-and-output.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>