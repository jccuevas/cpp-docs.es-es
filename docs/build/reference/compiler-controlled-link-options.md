---
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 21d0baccaf74fc08bb110b0ae9f8b7dc108abd6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561582"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

El compilador de CL llama automáticamente el vínculo a menos que especifique la opción /c. CL proporciona cierto control sobre el enlazador a través de las opciones de línea de comandos y argumentos. En la tabla siguiente se resume las características de CL que afectan a la vinculación.

|Especificación de CL|Acción de CL que afecta al vínculo|
|----------------------|---------------------------------|
|Cualquier extensión de nombre de archivo que no sea .def, .cpp, .cxx o .c|Pasa un nombre de archivo como entrada de LINK|
|*nombre de archivo*.def|Pasa/def:*filename*.def|
|/F*número*|Pasa/Stack:*número*|
|/FD*nombre de archivo*|Pasa/PDB:*nombre de archivo*|
|/Fe*nombre de archivo*|Pasa/OUT:*nombre de archivo*|
|/FM*nombre de archivo*|Pasa/Map:*nombre de archivo*|
|/Gy|Crea funciones empaquetadas (COMDAT); permite la vinculación de nivel de función|
|/LD|Pasa /DLL|
|/LDd|Pasa /DLL|
|/link|Pasa el resto de la línea de comandos al vínculo|
|/MD o/MT|Coloca un nombre de biblioteca predeterminado en el archivo .obj|
|/ MDd o /MTd|Coloca un nombre de biblioteca predeterminado en el archivo .obj. Define el símbolo **_DEBUG**|
|/nologo|Pasa /NOLOGO|
|/ Zd|Fases/Debug|
|Zi o/Z7|Fases/Debug|
|/Zl|Omite el nombre de la biblioteca predeterminada del archivo .obj|

Para obtener más información, consulte [Opciones del compilador](../../build/reference/compiler-options.md).

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)