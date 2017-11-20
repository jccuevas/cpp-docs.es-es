---
title: "-Z7, - Zi, - ZI (formato de la información de depuración) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 782420e674d6101f49e2b361c888a8f4b0b4c1ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Formato de la información de depuración)
Seleccione el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto (.obj) o en una base de datos de programa (PDB).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas opciones se describen en la siguiente tabla.  
  
 Ninguna  
 No se genera información de depuración, por lo que la compilación es más rápida.  
  
 **/ Z7**  
 Genera un archivo .obj que contiene información de depuración simbólica completa para usar con el depurador. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea. No se genera ningún archivo .pdb.  
  
 Para distribuidores de bibliotecas de otros fabricantes, no tener un archivo .pdb supone una ventaja. Sin embargo, los archivos .obj para los encabezados precompilados son necesarios durante la fase de vinculación y la depuración. Si sólo hay tipo información (y ningún código) en los archivos objeto .pch, también tendrá que compilar con [/Yl (Insertar referencia PCH para biblioteca de depuración)](../../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
 **/ Zi**  
 Genera una base de datos de programa (PDB) que contiene información de tipos e información de depuración simbólica que se usa con el depurador. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea.  
  
 **/ Zi** no afecta a las optimizaciones. Sin embargo, **/Zi** implica **/debug**; vea [/DEBUG (generar información de depuración)](../../build/reference/debug-generate-debug-info.md) para obtener más información.  
  
 La información de tipo se coloca en el archivo .pdb y no en el archivo .obj.  
  
 Puede usar [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) con **/Zi**, mientras que **/Gm** no está disponible cuando se compila con **/Z7**.  
  
 Cuando se compila con **/Zi** y **/CLR**, el <xref:System.Diagnostics.DebuggableAttribute> atributo no se coloca en los metadatos del ensamblado; debe especificar en el código fuente, si lo desea. Este atributo puede afectar al rendimiento de la aplicación en tiempo de ejecución. Para obtener más información acerca de cómo afecta el atributo Debuggable al rendimiento y cómo puede modificar el impacto en el rendimiento, consulte [facilitar una imagen para depuración](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).  
  
 **/ ZI**  
 Genera una base de datos de programa, como se describe anteriormente, con un formato compatible con la característica Editar y continuar. Si desea usar la depuración con Editar y continuar, debe usar esta opción. Dado que la mayoría de las optimizaciones es incompatible con Editar y continuar, uso **/Zi** deshabilita cualquier `#pragma optimize` las instrucciones en el código.  
  
 **/ Zi** hace [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) y [/FC (Full ruta de acceso del archivo de código fuente en diagnósticos)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) para su uso en la compilación.  
  
 **/ Zi** no es compatible con [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  **/ Zi** solo está disponible en los compiladores con destino procesadores x86 y x64; esta opción del compilador no está disponible en los compiladores con destino procesadores ARM.  
  
 El compilador asigna a la base de datos de programa *proyecto*.pdb. Si compila un archivo sin un proyecto, el compilador crea una base de datos denominada VC*x*0.pdb., donde *x* es la versión principal de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] en uso. El compilador incrusta el nombre de la PDB en cada archivo .obj que crea con esta opción y hace apuntar el depurador a la ubicación de la información simbólica y de números de línea. Si utiliza esta opción, los archivos .obj tendrán un tamaño menor, porque la información de depuración se almacena en el archivo .pdb y no en archivos .obj.  
  
 Si crea una biblioteca a partir de objetos compilados con esta opción, el archivo .pdb asociado debe estar disponible cuando se vincule la biblioteca a un programa. Por lo tanto, si distribuye la biblioteca, debe distribuir el archivo PDB.  
  
 Para crear una biblioteca que contiene información de depuración sin utilizar archivos .pdb, debe seleccionar C el compilador 7.0 Compatible (**/Z7**) opción. Si usa las opciones de encabezado precompilado, la información de depuración del encabezado precompilado y del resto del código fuente se incluye en el archivo PDB. El **/Yd** se omite cuando se especifica la opción de base de datos de programa.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **General** página de propiedades.  
  
4.  Modificar el **formato de información de depuración** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)