---
title: Propiedades del enlazador de Clang (C++ para Android)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 55b944040157d13741b992f4ec66c35d1b117d95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470254"
---
# <a name="clang-linker-properties-android-c"></a>Propiedades del enlazador de Clang (C++ para Android)

| Propiedad | Descripción | Opciones |
|--|--|--|
| Archivo de salida | La opción invalida el nombre y la ubicación predeterminados del programa que crea el enlazador. (-o) |
| Mostrar progreso | Imprime los mensajes de progreso del enlazador. |
| Versión | La opción -version indica al enlazador que agregue un número de versión en el encabezado del ejecutable. |
| Habilitar resultado detallado | La opción -verbose indica al enlazador que genere mensajes detallados para la depuración. |
| Habilitar vinculación incremental | La opción indica al enlazador que habilite la vinculación incremental. |
| Ruta de búsqueda de biblioteca compartida | Permite que el usuario rellene la ruta de búsqueda de bibliotecas compartidas. |
| Directorios de bibliotecas adicionales | Permite que el usuario invalide la ruta de acceso de la biblioteca del entorno. (Carpeta -L). |
| Informar de referencias de símbolos sin resolver | Esta opción cuando se habilita informa de las referencias de símbolos sin resolver. |
| Optimizar para uso de memoria | Optimizado para el uso de memoria, ya que vuelve a leer las tablas de símbolos cuando es necesario. |
| Omitir bibliotecas predeterminadas específicas | Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. |
| Forzar referencias de símbolos | Obliga a que los símbolos se especifiquen en el archivo de salida como no definidos. |
| Información del símbolo de depurador | Información del símbolo de depurador del archivo de salida. | **Incluir todos**<br /><br />**Omitir símbolos innecesarios para el proceso de reubicación**<br /><br />**Omitir solo información del símbolo del depurador**<br /><br />**Omitir información de todos los símbolos** |
| Información del símbolo del depurador de paquete | Quite la información de los símbolos del depurador antes de empaquetar.  Se utiliza una copia del binario original para la depuración. |
| Nombre de archivo de asignaciones | La opción Asignar indica al enlazador que cree un archivo de asignaciones con el nombre especificado por el usuario. |
| Marcar variables como de solo lectura después de la reubicación | Esta opción marca las variables como de solo lectura después de la reubicación. |
| Habilitar enlace de función inmediata | Esta opción marca el objeto para el enlace de función inmediata. |
| Requerir pila de ejecutable | Esta opción indica en la salida que no requiere una pila de ejecutable. |
| Archivo completo | El archivo completo usa todos los códigos de los orígenes y las dependencias adicionales. |
| Opciones adicionales | Opciones adicionales. |
| Dependencias adicionales | Especifica elementos adicionales que se agregarán a la línea de comandos del vínculo. |
| Dependencias de biblioteca | Esta opción permite especificar bibliotecas adicionales para agregarlas a la línea de comandos del vinculador. Las bibliotecas adicionales se agregan al final de la línea de comandos del vinculador comienzan con *lib* y terminan con *. a* o *. so* .  (-lFILE) |
