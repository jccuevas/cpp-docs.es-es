---
title: Archivos de definición de módulos (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 041894fa88527061d90399540bc29762bff66f81
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424540"
---
# <a name="module-definition-def-files"></a>Archivos de definición de módulos (.Def)

Archivos de definición de módulo (.def) proporcionan información acerca de las exportaciones, atributos y otra información sobre el programa que debe vincularse al vinculador. Un archivo .def es más útil cuando se crea un archivo DLL. Dado que hay [opciones del vinculador](../../build/reference/linker-options.md) que puede utilizarse en lugar de instrucciones de definición de módulos, archivos .def normalmente no son necesarios. También puede usar [__declspec (dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) como una manera de especificar las funciones exportadas.

Puede invocar un archivo .def durante la fase del enlazador con el [/DEF (especificar archivo de definición de módulos)](../../build/reference/def-specify-module-definition-file.md) opción del vinculador.

Si va a compilar un archivo .exe que no tiene exportaciones, mediante un archivo .def hará que su carga de grandes y más lento de archivos de salida.

Para obtener un ejemplo, vea [exportar desde un archivo DLL mediante archivos DEF](../../build/exporting-from-a-dll-using-def-files.md).

Consulte las secciones siguientes para obtener más información:

- [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTS](../../build/reference/exports.md)

- [HEAPSIZE](../../build/reference/heapsize.md)

- [LIBRARY](../../build/reference/library.md)

- [NAME](../../build/reference/name-c-cpp.md)

- [SECCIONES](../../build/reference/sections-c-cpp.md)

- [STACKSIZE](../../build/reference/stacksize.md)

- [STUB](../../build/reference/stub.md)

- [VERSION](../../build/reference/version-c-cpp.md)

- [Palabras reservadas](../../build/reference/reserved-words.md)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
