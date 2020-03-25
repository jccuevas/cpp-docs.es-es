---
title: Decoración de nombres
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173522"
---
# <a name="name-decoration"></a>Decoración de nombres

La decoración de nombres normalmente hace referencia a las convenciones de nomenclatura de C++, pero también se puede aplicar a varios casos de C. De forma predeterminada, C++ usa el nombre de la función, los parámetros y el tipo de valor devuelto para crear un nombre del vinculador para la función. Considere la siguiente declaración de función:

`void CALLTYPE test(void);`

En la tabla siguiente se muestra el nombre del vinculador para varias convenciones de llamada.

|Convención de llamada|`extern "C"` o `.c` archivo|`.cpp`, `.cxx` o `/TP`|
|------------------------|---------------------------|------------------------|
|Convención de nomenclatura de C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Convención de nomenclatura de llamada rápida (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Convención de nomenclatura de llamada estándar (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Convención de nomenclatura de llamadas vectoriales (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Utilice `extern "C"` para llamar a una función de C++C desde. `extern "C"` fuerza el uso de la Convención de nomenclatura de C para C++ funciones que no son de clase. Tenga en cuenta los modificadores de compilador **/TC** o **/TP**, que indican al compilador que omita la extensión de C++nombre de archivo y compile el archivo como C o, respectivamente. Estas opciones pueden dar lugar a nombres de enlazador que no se esperan.

Tener prototipos de función con parámetros no coincidentes también puede producir este error. La decoración de nombres incorpora los parámetros de una función en el nombre de función representativo final. Llamar a una función con los tipos de parámetro que no coinciden con los de la declaración de función también puede producir LNK2001.

Actualmente no hay ningún estándar para C++ asignar nombres entre proveedores de compiladores o incluso entre diferentes versiones de un compilador. La vinculación de archivos objeto compilados por otros compiladores puede no producir el mismo esquema de nomenclatura y puede producir externos sin resolver.

## <a name="see-also"></a>Consulte también

[Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
