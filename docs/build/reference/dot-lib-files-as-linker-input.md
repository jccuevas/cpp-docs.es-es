---
title: archivos .Lib como entrada del vinculador
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
ms.openlocfilehash: f3b2ae0d82e682cc89243b7b527ee6e0b51d4c3d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426776"
---
# <a name="lib-files-as-linker-input"></a>archivos .Lib como entrada del vinculador

LINK acepta bibliotecas estándar y COFF bibliotecas de importación, los cuales normalmente tienen la extensión. lib. Las bibliotecas estándar contienen objetos y se crean mediante la herramienta LIB. Las bibliotecas de importación contienen información acerca de las exportaciones en otros programas y se crean mediante el vínculo cuando compila un programa que contiene exportaciones o por la herramienta LIB. Para obtener información sobre el uso de LIB para crear estándar o bibliotecas de importación, vea [referencia de LIB](../../build/reference/lib-reference.md). Para obtener más información sobre el uso de vínculo para crear una biblioteca de importación, consulte el [/DLL](../../build/reference/dll-build-a-dll.md) opción.

Se especifica una biblioteca de vínculo como un argumento de nombre de archivo o una biblioteca de forma predeterminada. VÍNCULO resuelve referencias externas buscando en primer lugar en las bibliotecas especificadas en la línea de comandos y, después, en las bibliotecas especificadas con la [DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) opción, y, a continuación, en las bibliotecas predeterminadas mencionadas en los archivos .obj. Si se especifica una ruta de acceso con el nombre de la biblioteca, vínculo busca la biblioteca en ese directorio. Si no se especifica ninguna ruta de acceso, el vínculo busca primero en el directorio que se está ejecutando vínculo de y, a continuación, en los directorios especificados en la variable de entorno LIB.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Para agregar archivos .lib como entrada del vinculador en el entorno de desarrollo

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Elija la **entrada** página de propiedades de la **vinculador** carpeta.

1. Modificar el **dependencias adicionales** propiedad va a agregar los archivos .lib.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Para agregar mediante programación archivos .lib como entrada del vinculador

- Consulte [dependencias](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo crear y usar un archivo .lib. En primer lugar, cree un archivo .lib:

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

Y, a continuación, compile este ejemplo mediante el archivo .lib que acaba de crear:

```cpp
// lib_link_input_2.cpp
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp
__declspec(dllimport) int Test();
#include <iostream>
int main() {
   std::cout << Test() << std::endl;
}
```

```Output
213
```

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
