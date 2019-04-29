---
title: /DEBUG (Generar información de depuración)
ms.date: 11/04/2016
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
ms.openlocfilehash: ca7ef5d1935ddea0441f49e387e35184c6fd1fc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294023"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generar información de depuración)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>Comentarios

El **/DEBUG** opción crea información de depuración para el archivo ejecutable.

El vinculador coloca la información de depuración en un archivo de programa (PDB) de la base de datos. Actualiza el archivo PDB durante las compilaciones posteriores del programa.

Un archivo ejecutable (archivo .exe o DLL) creado para la depuración contiene el nombre y ruta de acceso del archivo PDB correspondiente. El depurador lee el nombre incrustado y usa el archivo PDB al depurar el programa. El vinculador utiliza el nombre base del programa y el archivo .pdb de extensión para el nombre de la base de datos de programa e incrusta la ruta de acceso donde se creó. Para invalidar este comportamiento predeterminado, establezca [/PDB](pdb-use-program-database.md) y especifique un nombre de archivo diferente.

El **/Debug: Fastlink** opción está disponible en Visual Studio 2017 y versiones posteriores. Esta opción deja la información de símbolos privados en los productos de compilación individuales utilizados para crear el ejecutable. Genera un archivo PDB limitado que se indiza en la información de depuración en los archivos objeto y bibliotecas que se usan para compilar el archivo ejecutable en lugar de hacer una copia completa. Esta opción se puede vincular de dos a cuatro veces más rápido que la generación de PDB completos y se recomienda cuando se depura localmente y tiene los productos de compilación disponibles. Esta PDB limitada no se puede usar para la depuración cuando los productos de compilación necesarios no están disponibles, como cuando se implementa el archivo ejecutable en otro equipo. En un símbolo del sistema de desarrollador, puede usar la herramienta mspdbcmf.exe para generar un archivo PDB completo desde esta PDB limitada. En Visual Studio, utilice los elementos del menú proyecto o de compilación para generar un archivo PDB completo para crear un archivo PDB completo para el proyecto o solución.

El **/Debug: full** opción mueve toda la información de símbolos privados de productos de compilación individuales (archivos objeto y bibliotecas) en un archivo PDB único y puede ser la parte más lenta del vínculo. Sin embargo, el archivo PDB completo puede utilizarse para depurar el archivo ejecutable cuando no hay otros productos de compilación están disponibles, por ejemplo, cuando se implementa el archivo ejecutable.

El **/DEBUG: Ninguno** opción no genera un archivo PDB.

Al especificar **/DEBUG** sin opciones adicionales, el enlazador predeterminado es **/Debug: full** para versiones de archivo MAKE y línea de comandos, para la versión se basa en el IDE de Visual Studio y para depuración y lanzamiento se basa en Visual Studio 2015 y versiones anteriores. A partir de Visual Studio 2017, el sistema de compilación en el IDE tiene como valor predeterminado **/Debug: Fastlink** al especificar el **/DEBUG** opción para las compilaciones de depuración. Otros valores predeterminados son los mismos para mantener la compatibilidad con versiones anteriores.

El compilador [compatible con C7](z7-zi-zi-debug-information-format.md) (/ Z7) opción hace que el compilador deje la información de depuración en los archivos .obj. También puede usar el [base de datos de programa](z7-zi-zi-debug-information-format.md) opción del compilador (/Zi) para almacenar la información de depuración en un archivo PDB para el archivo .obj. El vinculador busca la PDB del objeto primero en la ruta de acceso absoluta que se escriben en el archivo .obj y, a continuación, en el directorio que contiene el archivo .obj. No se puede especificar el nombre del archivo PDB de un objeto o la ubicación al vinculador.

[/ INCREMENTAL](incremental-link-incrementally.md) está implícita cuando se especifica/debug.

/ DEBUG cambia los valores predeterminados para el [/OPT](opt-optimizations.md) opción de REF a NOREF y de ICF a NOICF, por lo que si desea que los valores predeterminados originales, debe especificar explícitamente/OPT: REF o/OPT: ICF.

No es posible crear .exe o .dll que contiene información de depuración. Depurar información siempre se coloca en un archivo .obj o PDB.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depuración** página de propiedades.

1. Modificar el **generar información de depuración** propiedad para habilitar la generación de PDB. Esto permite/Debug: Fastlink de forma predeterminada en Visual Studio 2017.

1. Modificar el **generar archivo de base de datos de programa completa** propiedad para habilitar/Debug: Full para la generación de PDB completos para cada compilación incremental.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
