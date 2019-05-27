---
title: /DEBUG (Generar información de depuración)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
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
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837142"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generar información de depuración)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>Comentarios

La opción **/DEBUG** crea información de depuración para el archivo ejecutable.

El enlazador coloca la información de depuración en un archivo de base de datos del programa (PDB). Actualiza el archivo PDB durante las compilaciones posteriores del programa.

Un archivo ejecutable (archivo .exe o DLL) creado para la depuración contiene el nombre y la ruta de acceso del archivo PDB correspondiente. El depurador lee el nombre insertado y usa el archivo PDB al depurar el programa. El enlazador usa el nombre base del programa y la extensión .pdb para dar un nombre a la base de datos del programa, e inserta la ruta de acceso donde se creó. Para invalidar este comportamiento predeterminado, establezca [/PDB](pdb-use-program-database.md) y especifique un nombre de archivo diferente.

La opción **/DEBUG:FASTLINK** está disponible en Visual Studio 2017 y versiones posteriores. Esta opción deja la información de símbolos privados en los productos de compilación individuales usados para crear el ejecutable. Genera un archivo PDB limitado que se indiza en la información de depuración en los archivos objeto y las bibliotecas usadas para compilar el archivo ejecutable en lugar de hacer una copia completa. Esta opción se puede vincular de dos a cuatro veces más rápido que la generación del archivo PDB completo y se recomienda cuando se depura localmente y se tienen los productos de compilación disponibles. Este archivo PDB limitado no se puede usar para la depuración cuando los productos de compilación necesarios no están disponibles, como cuando se implementa el archivo ejecutable en otro equipo. En un símbolo del sistema de desarrollador, puede usar la herramienta mspdbcmf.exe para generar un archivo PDB completo desde este archivo PDB limitado. En Visual Studio, use los elementos del menú Proyecto o Compilación para generar un archivo PDB completo para el proyecto o la solución.

La opción **/DEBUG:FULL** mueve toda la información de símbolos privados de productos de compilación individuales (archivos objeto y bibliotecas) a un archivo PDB único y puede ser la parte más lenta del vínculo. Pero tenga en cuenta que puede usar el archivo PDB completo para depurar el archivo ejecutable cuando no hay otros productos de compilación disponibles, como por ejemplo, cuando se implementa el archivo ejecutable.

La opción **/DEBUG:NONE** no genera un archivo PDB.

Al especificar **/DEBUG** sin opciones adicionales, el enlazador tiene como valor predeterminado **/DEBUG:FULL** para compilaciones de archivos Make y línea de comandos, para compilaciones de versión en el IDE de Visual Studio y para depuración y versiones de compilación en Visual Studio 2015 y versiones anteriores. A partir de Visual Studio 2017, el sistema de compilación en el IDE tiene como valor predeterminado **/DEBUG:FASTLINK** al especificar la opción **/DEBUG** para las compilaciones de depuración. No se cambian otros valores predeterminados para mantener la compatibilidad con versiones anteriores.

La opción [Compatible con C7](z7-zi-zi-debug-information-format.md) (/Z7) del compilador hace que el compilador deje la información de depuración en los archivos .obj. También puede usar la opción del compilador [Base de datos de programa](z7-zi-zi-debug-information-format.md) para almacenar la información de depuración en un archivo PDB para el archivo .obj. El enlazador busca primero el archivo PDB del objeto en la ruta de acceso absoluta que se escribe en el archivo .obj y, después, en el directorio que contiene el archivo .obj. No se puede especificar un nombre de archivo PDB o una ubicación de un objeto al enlazador.

La opción [/INCREMENTAL](incremental-link-incrementally.md) está implícita cuando se especifica /DEBUG.

/DEBUG cambia los valores predeterminados para la opción [/OPT](opt-optimizations.md) de REF a NOREF y de ICF a NOICF, por lo que si quiere los valores predeterminados originales, debe especificar explícitamente /OPT:REF o /OPT:ICF.

No es posible crear un archivo .exe o .dll que contenga información de depuración. La información de depuración siempre se coloca en un archivo .obj o .pdb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **Depuración**.

1. Modifique la propiedad **Generar información de depuración** para habilitar la generación del archivo PDB. Esto habilita /DEBUG:FASTLINK de forma predeterminada en Visual Studio 2017 y versiones posteriores.

1. Modifique la propiedad **Generar archivo de base de datos de programa completa** para habilitar /DEBUG:FULL para la generación completa del archivo PDB en cada compilación incremental.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
