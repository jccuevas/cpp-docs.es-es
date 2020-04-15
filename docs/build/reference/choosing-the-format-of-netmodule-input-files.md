---
title: Elegir el formato de los archivos de entrada .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320573"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Elegir el formato de los archivos de entrada .netmodule

Un archivo .obj MSIL (compilado con [/clr](clr-common-language-runtime-compilation.md)) también se puede utilizar como un archivo .netmodule.  Los archivos .obj contienen metadatos y símbolos nativos.  .netmodules solo contienen metadatos.

Puede pasar un archivo MSIL .obj a cualquier otro compilador de Visual Studio a través de la opción del compilador /addmodule (pero tenga en cuenta que el archivo .obj pasa a formar parte del ensamblado resultante y debe enviarse con el ensamblado).  Por ejemplo, Visual C- y Visual Basic tienen la opción del compilador /addmodule.

> [!NOTE]
> En la mayoría de los casos, deberá pasar al vinculador el archivo .obj de la compilación que creó el módulo .net.  Pasar un archivo de módulo MSIL .dll o .netmodule al vinculador puede dar lugar a LNK1107.

Los archivos .obj, junto con sus archivos .h asociados, a los que se hace referencia a través de #include en el origen, permiten que las aplicaciones C++ consuman los tipos nativos en el módulo, mientras que en un archivo .netmodule, solo los tipos administrados pueden ser consumidos por una aplicación C++.  Si intenta pasar un archivo .obj a #using, la información sobre tipos nativos no estará disponible; #include en su lugar el archivo .h del archivo .obj.

Otros compiladores de Visual Studio solo pueden consumir tipos administrados desde un módulo.

Utilice lo siguiente para determinar si necesita utilizar un archivo .netmodule o .obj como entrada de módulo para el vinculador MSVC:

- Si va a compilar con un compilador de Visual Studio distinto de Visual C++, genere un .netmodule y use el .netmodule como entrada para el vinculador.

- Si utiliza el compilador MSVC para generar módulos y si los módulos se usarán para crear algo distinto de una biblioteca, utilice los archivos .obj generados por el compilador como entrada de módulo para el vinculador; no utilice el archivo .netmodule como entrada.

- Si los módulos se utilizarán para crear una biblioteca nativa (no administrada), utilice archivos .obj como entrada de módulo para el vinculador y genere un archivo de biblioteca .lib.

- Si los módulos se utilizarán para crear una biblioteca administrada y si toda la entrada del módulo en el vinculador será verificable (producida con /clr:safe), utilice archivos .obj como entrada de módulo para el vinculador y genere un archivo de biblioteca .dll (ensamblaje) o .netmodule (módulo).

- Si los módulos se utilizarán para crear una biblioteca administrada, y si se generarán uno o más módulos de entrada en el vinculador con solo /clr, utilice archivos .obj como entrada de módulo para el vinculador y genere un archivo .dll (ensamblaje).  Si desea exponer tipos administrados de la biblioteca y si también desea que las aplicaciones C++ consuman los tipos nativos de la biblioteca, la biblioteca constará de los archivos .obj para los módulos de componentes de bibliotecas (también querrá enviar los archivos .h para cada módulo, para que se pueda hacer referencia a ellos con #include desde el código fuente).

## <a name="see-also"></a>Consulte también

[Archivos .netmodule como entrada del vinculador](netmodule-files-as-linker-input.md)
