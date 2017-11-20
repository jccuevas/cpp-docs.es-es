---
title: "-DEBUG (generar información de depuración) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs: C++
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5752b6ab9f2af7c54aedc611eaae2b7f98b75ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generar información de depuración)
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>Comentarios  

El **/DEBUG** opción crea información de depuración para el archivo ejecutable.    
  
El vinculador coloca la información de depuración en un archivo de programa (PDB) de la base de datos. Actualiza el archivo PDB durante las compilaciones posteriores del programa.  
  
Un archivo ejecutable (archivo .exe o .dll) creado para la depuración contiene el nombre y la ruta de acceso del archivo PDB correspondiente. El depurador lee el nombre incrustado y utiliza el archivo PDB al depurar el programa. El vinculador utiliza el nombre base del programa y el archivo .pdb de extensión para el nombre de la base de datos de programa e incrusta la ruta de acceso donde se creó. Para invalidar este comportamiento predeterminado, establezca [/PDB](../../build/reference/pdb-use-program-database.md) y especifique un nombre de archivo diferente.  

El **/Debug: Fastlink** opción deja la información de símbolos privados en los productos de compilación individuales que se usan para compilar el archivo ejecutable. Genera un archivo PDB limitado que inserta un índice en la información de depuración en los archivos objeto y bibliotecas se utilizan para compilar el archivo ejecutable en lugar de realizar una copia completa. Esta opción puede vincular entre dos y cuatro veces más rápido que la generación de PDB completos y se recomienda si se depura localmente y necesita los productos de compilación disponibles. Esta PDB limitada no se puede usar para la depuración cuando los productos de compilación necesarios no están disponibles, como cuando el ejecutable se implementa en otro equipo. En un símbolo del sistema de desarrollador, puede usar la herramienta mspdbcmf.exe para generar un archivo PDB completo desde esta PDB limitada. En Visual Studio, utilice los elementos de menú de proyecto o de la compilación para generar un archivo PDB completo para crear un archivo PDB completa para el proyecto o solución.  
  
El **/Debug: full** opción mueve toda la información de símbolos privados de productos de compilación individuales (archivos objeto y bibliotecas) en un archivo PDB único y puede ser la parte más lenta del vínculo. Sin embargo, el archivo PDB completo puede utilizarse para depurar el archivo ejecutable cuando no hay otros productos de compilación están disponibles, por ejemplo, cuando se implementa el archivo ejecutable.  
  
El **/DEBUG: Ninguno** opción no genera un archivo PDB.  
  
Cuando se especifica **/DEBUG** sin ninguna opción adicional, el vinculador usa de forma predeterminada **/Debug: full** para compilaciones de archivo MAKE y línea de comandos, versión de compilaciones en el IDE de Visual Studio y de lanzamiento y depuración se basa en Visual Studio 2015 y versiones anteriores. A partir de 2017 de Visual Studio, el sistema de compilación en el IDE tiene como valor predeterminado **/Debug: Fastlink** cuando se especifica la **/DEBUG** opción para las compilaciones de depuración. Otros valores predeterminados no se han modificado para mantener la compatibilidad con versiones anteriores.  
  
El compilador [compatible con C7](../../build/reference/z7-zi-zi-debug-information-format.md) (/ Z7) opción hace que el compilador deje la información de depuración en los archivos .obj. También puede usar el [base de datos de programa](../../build/reference/z7-zi-zi-debug-information-format.md) opción del compilador (/Zi) para almacenar la información de depuración en un archivo PDB del archivo .obj. El vinculador busca la PDB del objeto primero en la ruta de acceso absoluta escrita en el archivo .obj y, a continuación, en el directorio que contiene el archivo .obj. No se puede especificar el nombre del archivo PDB de un objeto o la ubicación al vinculador.  
  
[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md) está implícita cuando se especifica/debug.  
  
/ DEBUG cambia los valores predeterminados para la [/OPT](../../build/reference/opt-optimizations.md) opción de REF a NOREF y de ICF a NOICF, por lo que si desea que los valores predeterminados originales, debe especificar explícitamente/OPT: REF o/OPT: ICF.  
  
No es posible crear .exe o .dll que contiene información de depuración. Depurar información siempre se coloca en un archivo .obj o .pdb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **depuración** página de propiedades.  
  
4.  Modificar el **generar información de depuración** propiedad para habilitar la generación de PDB. Esto permite/Debug: Fastlink de forma predeterminada en Visual Studio de 2017.  
  
4.  Modificar el **generar archivo de base de datos de programa completo** propiedad para permitir/Debug: Full para la generación completa de PDB para cada compilación incremental.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
