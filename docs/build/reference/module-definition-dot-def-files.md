---
title: Archivos de definición de módulos (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812244"
---
# <a name="module-definition-def-files"></a>Archivos de definición de módulos (.Def)

Archivos de definición de módulo (.def) proporcionan información acerca de las exportaciones, atributos y otra información sobre el programa que debe vincularse al vinculador. Un archivo .def es más útil cuando se crea un archivo DLL. Dado que hay [las opciones del vinculador MSVC](linker-options.md) que puede utilizarse en lugar de instrucciones de definición de módulos, archivos .def normalmente no son necesarios. También puede usar [__declspec (dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) como una manera de especificar las funciones exportadas.

Puede invocar un archivo .def durante la fase del enlazador con el [/DEF (especificar archivo de definición de módulos)](def-specify-module-definition-file.md) opción del vinculador.

Si va a compilar un archivo .exe que no tiene exportaciones, mediante un archivo .def hará que su carga de grandes y más lento de archivos de salida.

Para obtener un ejemplo, vea [exportar desde un archivo DLL mediante archivos DEF](../exporting-from-a-dll-using-def-files.md).

Consulte las secciones siguientes para obtener más información:

- [Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)

- [EXPORTS](exports.md)

- [HEAPSIZE](heapsize.md)

- [LIBRARY](library.md)

- [NAME](name-c-cpp.md)

- [SECCIONES](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [VERSION](version-c-cpp.md)

- [Palabras reservadas](reserved-words.md)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
