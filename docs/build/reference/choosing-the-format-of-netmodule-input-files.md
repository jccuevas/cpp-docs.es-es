---
title: Elegir el formato de los archivos de entrada .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: d48bfe84210143db333d1e6b081acf1aa66980cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294582"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Elegir el formato de los archivos de entrada .netmodule

Un archivo .obj MSIL (compilado con [/CLR](clr-common-language-runtime-compilation.md)) también puede usarse como un archivo .netmodule.  los archivos .obj contienen metadatos y símbolos nativos.  archivos .netmodule sólo contienen metadatos.

Puede pasar un archivo .obj MSIL a cualquier otro compilador de Visual Studio mediante la opción del compilador/addmodule (pero tenga en cuenta que el archivo .obj pasa a formar parte del ensamblado resultante y se debe enviar con el ensamblado).  Por ejemplo, Visual C# y Visual Basic tienen la opción del compilador/addmodule.

> [!NOTE]
>  En la mayoría de los casos, deberá pasar al vinculador el archivo .obj de la compilación que creó el módulo. NET.  Pasar un archivo de módulo de archivo .dll o .netmodule MSIL al vinculador puede producir el error LNK1107.

los archivos .obj, junto con sus archivos .h asociados, que se hace referencia a través de #include en origen, permitir que las aplicaciones de C++ consumir los tipos nativos en el módulo, mientras que en un archivo .netmodule, solo los tipos administrados pueden utilizarse en una aplicación de C++.  Si intenta pasar un archivo .obj para #using, información sobre los tipos nativos no estará disponible; #include el archivo .h del archivo .obj en su lugar.

Otros compiladores de Visual Studio solo pueden consumir tipos administrados desde un módulo.

Para determinar si necesita usar un archivo .netmodule o un archivo .obj como entrada de módulo al vinculador MSVC, use lo siguiente:

- Si va a compilar con un compilador de Visual Studio distinto de Visual C++, genere un archivo .netmodule y úselo como entrada del vinculador.

- Si usa el compilador de MSVC para crear módulos y si los módulos se usará para crear algo distinto de una biblioteca, use los archivos .obj creados por el compilador como entrada de módulo al vinculador; No utilice el archivo .netmodule como entrada.

- Si los módulos se usará para compilar una biblioteca nativa (no administrado), use archivos .obj como entrada de módulo al vinculador y genere un archivo de biblioteca .lib.

- Si los módulos que se usará para crear una biblioteca administrada, y todas las entradas de módulo al vinculador será comprobable (generado con/CLR: safe), use archivos .obj como entrada de módulo al vinculador y generar un archivo .dll (ensamblado) o el archivo de biblioteca .netmodule (módulo).

- Si los módulos que se usará para crear una biblioteca administrada, y se generará una o varias entradas módulos del vinculador simplemente con/CLR, use archivos .obj como entrada de módulo al vinculador y genere un archivo .dll (ensamblado).  Si desea exponer tipos administrados desde la biblioteca y si también desea consumir los tipos nativos en la biblioteca de aplicaciones de C++, la biblioteca constará de los archivos .obj para los módulos de componente de bibliotecas (también deberá distribuir los archivos .h para cada módulo por lo que pueden hacer referencia a con #include de código fuente).

## <a name="see-also"></a>Vea también

[Archivos .netmodule como entrada del vinculador](netmodule-files-as-linker-input.md)
