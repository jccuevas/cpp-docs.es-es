---
title: Opciones de LINK controladas por el compilador
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440109"
---
# <a name="compiler-controlled-link-options"></a>Opciones de LINK controladas por el compilador

El compilador de CL llama automáticamente a LINK a menos que especifique la opción/c. CL proporciona cierto control sobre el enlazador a través de las opciones de línea de comandos y los argumentos. En la tabla siguiente se resumen las características de CL que afectan a la vinculación.

|Especificación de CL|Acción de CL que afecta a LINK|
|----------------------|---------------------------------|
|Cualquier extensión de nombre de archivo distinta de. c,. CXX,. cpp o. def|Pasa un nombre de archivo como entrada para el vínculo|
|*nombre de archivo*. def|Pasa/DEF:*filename*. def|
|/F*número*|Pasa/STACK:*número*|
|/FD*nombreDeArchivo*|Pasa/PDB:*filename*|
|/Fe*nombreDeArchivo*|Pasa/OUT:*nombrearchivo*|
|/FM*nombreDeArchivo*|Pasa/MAP:*filename*|
|/Gy|Crea funciones empaquetadas (COMDAT); habilita la vinculación en el nivel de función|
|/LD|Pasa/DLL|
|/LDd|Pasa/DLL|
|/link|Pasa el resto de la línea de comandos a LINK|
|/MD o/MT|Coloca un nombre de biblioteca predeterminado en el archivo. obj|
|/MDd o/MTd|Coloca un nombre de biblioteca predeterminado en el archivo. obj. Define el símbolo **_DEBUG**|
|/nologo|Pasa/NOLOGO|
|/Zd|Pasa/DEBUG|
|/Zi o/Z7|Pasa/DEBUG|
|/Zl|Omite el nombre de biblioteca predeterminado del archivo. obj|

Para obtener más información, vea [Opciones del compilador MSVC](compiler-options.md).

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
