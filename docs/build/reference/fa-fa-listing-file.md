---
title: / FA, /Fa (archivo de lista) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4014c58a7e562aa632dba62dcac04c835352cbf
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101734"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Archivo de lista)

Crea un archivo de lista que contiene el código ensamblador.

## <a name="syntax"></a>Sintaxis

> **/FA**[**c**\][**s**\][**u**] **/Fa**_pathname_

## <a name="remarks"></a>Comentarios

El **/FA** opción del compilador genera un archivo de lista del ensamblador para cada unidad de traducción en la compilación, que suele corresponde a un archivo de código fuente de C o C++. De forma predeterminada, sólo ensamblador se incluye en el archivo de lista, que se codifica como ANSI. El elemento opcional **c**, **s**, y **u** argumentos **/FA** control de código máquina si o código fuente son el resultado junto con el ensamblador enumerar, y si la lista está codificada como UTF-8.

De forma predeterminada, cada archivo de lista obtiene el mismo nombre base que el archivo de origen y tiene una extensión de ASM. Cuando se incluye código máquina mediante el **c** opción, el archivo de lista tiene una extensión .cod. Puede cambiar el nombre y la extensión de archivo de la lista y el directorio donde se crea mediante el uso de la **/Fa** opción.

### <a name="fa-arguments"></a>/FA argumentos

ninguna  
Lenguaje de ensamblador solo se incluye en la lista.

**c**  
Opcional. Incluye código máquina en la lista.

**s**  
Opcional. Incluye código fuente en la lista.

**u**  
Opcional. Codifica el archivo de lista en formato UTF-8 e incluye un marcador de orden de bytes. De forma predeterminada, el archivo está codificado como ANSI. Use `u` para crear un archivo de lista que se muestra correctamente en cualquier sistema, o si usa Unicode archivos de código fuente como entrada para el compilador.

Si ambos **s** y **u** se especifican y si un origen de archivo de código utiliza una codificación Unicode distintos de UTF-8 y, a continuación, las líneas de código en el archivo .asm podrían no mostrarse correctamente.

### <a name="fa-argument"></a>Argumento /FA

ninguna  
Una *origen*archivo .asm se crea para cada archivo de código fuente en la compilación.

*filename*  
Un archivo de lista denominado *filename*.asm se coloca en el directorio actual. Esto solo es válido cuando se compila un archivo de código fuente único.

*FileName.Extension*  
Un archivo de lista denominado *filename.extension* se coloca en el directorio actual. Esto solo es válido cuando se compila un archivo de código fuente único.

*Directorio*__\\__  
Una *archivo_origen*archivo .asm se crea y se colocan en la instancia especificada *directory* para cada archivo de código fuente en la compilación. Tenga en cuenta la barra diagonal necesaria. Se permiten rutas de acceso sólo en el disco actual.

*directorio*__\\__*nombre de archivo*  
Un archivo de lista denominado *filename*.asm se coloca en la instancia especificada *directory*. Esto solo es válido cuando se compila un archivo de código fuente único.

*directorio*__\\__*filename.extension*  
Un archivo de lista denominado *filename.extension* se coloca en la instancia especificada *directory*. Esto solo es válido cuando se compila un archivo de código fuente único.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

2. Seleccione el **propiedades de configuración** > **C o C++** > **archivos de salida** página de propiedades.

3. Modificar el **salida del ensamblador** propiedad para establecer el **/fac** y **/FAS** opciones para el ensamblador de máquina y código fuente. Modificar el **Unicode de uso para enumerar de ensamblador** propiedad para establecer el **/FAu** opción de salida ANSI y UTF-8. Modificar el **ubicación de la lista ASM** para establecer el **/Fa** opción para mostrar el nombre de archivo y ubicación.

Tenga en cuenta que si se establecen **salida del ensamblador** y **Unicode de uso para enumerar de ensamblador** propiedades pueden provocar [advertencia de la línea de comandos D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Para combinar estas opciones en el IDE, utilice el **opciones adicionales** campo el **línea de comandos** página en su lugar.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> o <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Para especificar **/FAu**, consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Ejemplo
La siguiente línea de comandos genera un origen combinado y listado de código máquina denominada HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>Vea también

[Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer opciones del compilador](../../build/reference/setting-compiler-options.md)   
[Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)