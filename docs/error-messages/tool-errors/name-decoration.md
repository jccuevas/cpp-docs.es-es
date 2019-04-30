---
title: Decoración de nombres
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393160"
---
# <a name="name-decoration"></a>Decoración de nombres

La decoración de nombres normalmente hace referencia a las convenciones de nomenclatura de C++, pero también se puede aplicar a varios casos de C. De forma predeterminada, C++ usa el nombre de la función, los parámetros y el tipo de valor devuelto para crear un nombre del vinculador para la función. Tenga en cuenta la siguiente declaración de función:

`void CALLTYPE test(void);`

En la tabla siguiente se muestra el nombre del vinculador para varias convenciones de llamada.

|Convención de llamada|`extern "C"` o `.c` archivo|`.cpp`, `.cxx` o `/TP`|
|------------------------|---------------------------|------------------------|
|Convención de nomenclatura de C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Convención de nomenclatura de llamada rápida (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Estándar de llamar a la convención de nomenclatura (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Convención de nomenclatura de llamada de vector (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Use `extern "C"` para llamar a una función de C desde C++. `extern "C"` fuerza el uso de la convención de nomenclatura de C para que no son de clase C++ funciones. Tenga en cuenta los modificadores de compilador **/TC** o **/Tp**, que indican al compilador que omita la extensión de nombre de archivo y compile el archivo como C o C++, respectivamente. Estas opciones pueden dar lugar a nombres vinculador que no espera.

Tener prototipos de función con parámetros no coincidentes también puede producir este error. La decoración de nombres incorpora los parámetros de una función en el nombre de función representativo final. Llamar a una función con los tipos de parámetro que no coinciden con los de la declaración de función también puede generar el error LNK2001.

Actualmente no hay ningún estándares para C++ denominación entre fabricantes de compiladores o incluso entre diferentes versiones de un compilador. Vincular archivos objeto compilados por otros compiladores puede no producir el mismo esquema de nomenclatura y puede causar externos sin resolver.

## <a name="see-also"></a>Vea también

[Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)