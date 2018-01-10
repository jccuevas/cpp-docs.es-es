---
title: / FA, /Fa (archivo de lista) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs: C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0cd569cf16e7b2a14faaa119eacaef0994d09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Archivo de lista)
Crea un archivo de lista que contiene el código ensamblador.  
  
## <a name="syntax"></a>Sintaxis  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/FA**_ruta de acceso_  
  
## <a name="remarks"></a>Comentarios  
El `/FA` opción del compilador genera un archivo de lista de ensamblador para cada unidad de traducción en la compilación, que suele corresponde a un archivo de código fuente de C o C++. De forma predeterminada, sólo ensamblador se incluye en el archivo de lista, que se codifica como ANSI. Opcional `c`, `s`, y `u` argumentos `/FA` control automático si el código o código fuente son salida junto con el ensamblador de lista y, si la lista está codificada como UTF-8.  
  
De forma predeterminada, cada archivo de lista recibe el mismo nombre base que el archivo de origen y tiene una extensión de ASM. Cuando se incluye código máquina utilizando el `c` opción, el archivo de lista tiene una extensión de .cod. Puede cambiar el nombre y la extensión del archivo de lista y el directorio donde se crea utilizando el `/Fa` opción.  

### <a name="fa-arguments"></a>/FA argumentos  
ninguna  
Lenguaje de ensamblador solo se incluye en la lista.  
  
`c`  
Opcional. Incluye código máquina en la lista.  
  
`s`  
Opcional. Incluye código fuente en la lista.  
  
`u`Es opcional. Codifica el archivo de lista en formato UTF-8 e incluye un marcador de orden de bytes. De forma predeterminada, el archivo está codificado como ANSI. Use `u` para crear un archivo de lista que se muestre correctamente en cualquier sistema, o si utiliza Unicode archivos de código fuente como entrada para el compilador.  
  
Si ambos `s` y `u` se especifican y si un origen de archivo de código utiliza una codificación Unicode de UTF-8 y, a continuación, las líneas de código en el archivo de ASM podrían no mostrarse correctamente.  
  
### <a name="fa-argument"></a>/FA argumento  
ninguna  
Una *origen*archivo asm se crea para cada archivo de código fuente en la compilación.  
  
*nombre de archivo* un archivo de lista denominado *filename*asm se coloca en el directorio actual. Esto solo es válido cuando se compila un archivo de código de origen único.  
  
*FileName.Extension*  
Un archivo de lista denominado *filename.extension* se coloca en el directorio actual. Esto solo es válido cuando se compila un archivo de código de origen único.  
  
*directorio*\  
Una *source_file*archivo asm se crea y se coloca en el especificado *directory* para cada archivo de código fuente en la compilación. Tenga en cuenta la barra diagonal necesaria. Se permiten rutas de acceso sólo en el disco actual.  
  
*directorio*\\*filename* un archivo de lista denominado *filename*asm se coloca en especificado *directory*. Esto solo es válido cuando se compila un archivo de código de origen único.  
  
*directorio*\\*filename.extension*  
Un archivo de lista denominado *filename.extension* se coloca en el especificado *directory*. Esto solo es válido cuando se compila un archivo de código de origen único.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Abra la **C/C++** carpeta y seleccione la **archivos de salida** página de propiedades.  
  
3.  Modificar el **resultado del ensamblador** propiedad para establecer el `/FAc` y `/FAs` opciones para ensamblador, automático y código fuente. Modificar el **Unicode de uso para enumerar de ensamblador** propiedad para establecer el `/FAu` opción para la salida de ANSI o UTF-8. Modificar el **ubicación de la lista ASM** para establecer el `/Fa` opción para mostrar el nombre de archivo y la ubicación.  
  
Tenga en cuenta que si se establecen **resultado del ensamblador** y **Unicode de uso para enumerar de ensamblador** pueden producir propiedades [advertencia de línea de comandos D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Para combinar estas opciones en el IDE, utilice el **opciones adicionales** campo el **línea de comandos** página de propiedades en su lugar.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> o <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Para especificar `/FAu`, consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Ejemplo  
La siguiente línea de comandos genera un origen combinado y lista de código máquina denominada HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)