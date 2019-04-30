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
ms.openlocfilehash: bc7a6cc596f138daa373042abca51642c24cf737
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342860"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

El compilador de CL llama automáticamente el vínculo a menos que especifique la opción /c. CL proporciona cierto control sobre el enlazador a través de las opciones de línea de comandos y argumentos. En la tabla siguiente se resume las características de CL que afectan a la vinculación.

|Especificación de CL|Acción de CL que afecta al vínculo|
|----------------------|---------------------------------|
|Cualquier extensión de nombre de archivo que no sea .def, .cpp, .cxx o .c|Pasa un nombre de archivo como entrada de LINK|
|*filename*.def|Pasa/def:*filename*.def|
|/F*number*|Pasa/Stack:*número*|
|/Fd*filename*|Pasa/PDB:*nombre de archivo*|
|/Fe*filename*|Pasa/OUT:*nombre de archivo*|
|/Fm*filename*|Pasa/Map:*nombre de archivo*|
|/Gy|Crea funciones empaquetadas (COMDAT); permite la vinculación de nivel de función|
|/LD|Pasa /DLL|
|/LDd|Pasa /DLL|
|/link|Pasa el resto de la línea de comandos al vínculo|
|/MD o/MT|Coloca un nombre de biblioteca predeterminado en el archivo .obj|
|/ MDd o /MTd|Coloca un nombre de biblioteca predeterminado en el archivo .obj. Define el símbolo **_DEBUG**|
|/nologo|Pasa /NOLOGO|
|/Zd|Fases/Debug|
|Zi o/Z7|Fases/Debug|
|/Zl|Omite el nombre de la biblioteca predeterminada del archivo .obj|

Para obtener más información, consulte [opciones del compilador MSVC](compiler-options.md).

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
