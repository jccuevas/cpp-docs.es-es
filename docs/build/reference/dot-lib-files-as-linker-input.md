---
title: . Lib archivos como entrada del vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8382e43398c4b6e5241542e6b41fdee8e2f70eff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374549"
---
# <a name="lib-files-as-linker-input"></a>archivos .Lib como entrada del vinculador
LINK acepta bibliotecas estándar y COFF bibliotecas de importación, que normalmente tienen la extensión. lib. Bibliotecas estándar contienen objetos y se crean mediante la herramienta LIB. Bibliotecas de importación contienen información acerca de las exportaciones en otros programas y se crean por el vínculo cuando compila un programa que contiene exportaciones o la herramienta LIB. Para obtener información sobre cómo utilizar LIB para crear estándar o bibliotecas de importación, consulte [referencia de LIB](../../build/reference/lib-reference.md). Para obtener más información sobre el uso de vínculo para crear una biblioteca de importación, vea la [/DLL](../../build/reference/dll-build-a-dll.md) opción.  
  
Una biblioteca se especifica al vínculo como un argumento de nombre de archivo o una biblioteca de forma predeterminada. VÍNCULO resuelve referencias externas buscando en primer lugar en las bibliotecas especificadas en la línea de comandos, a continuación, en las bibliotecas especificadas con la [DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) opción, y, a continuación, en las bibliotecas predeterminadas mencionadas en los archivos .obj. Si se especifica una ruta de acceso con el nombre de la biblioteca, vínculo busca la biblioteca en ese directorio. Si no se especifica ninguna ruta de acceso, LINK buscará primero en el directorio que se está ejecutando vínculo desde y, a continuación, en los directorios especificados en la variable de entorno LIB.  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Para agregar archivos .lib como entrada del vinculador en el entorno de desarrollo  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Elija la **entrada** página de propiedades de la **vinculador** carpeta.  
  
3.  Modificar el **dependencias adicionales** propiedad que se va a agregar los archivos .lib.  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Para agregar mediante programación archivos .lib como entrada del vinculador  
  
-   Vea [dependencias](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente muestra cómo crear y usar un archivo .lib. En primer lugar, generar un archivo .lib:  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
Y, a continuación, compilar este ejemplo mediante el archivo .lib que acaba de crear:  
  
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
 [Archivos de entrada de vínculo](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)