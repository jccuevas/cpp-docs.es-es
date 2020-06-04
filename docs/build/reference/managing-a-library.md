---
title: Administrar una biblioteca
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336406"
---
# <a name="managing-a-library"></a>Administrar una biblioteca

El modo predeterminado para LIB es crear o modificar una biblioteca de objetos COFF. LIB se ejecuta en este modo cuando no se especifica /EXTRACT (para copiar un objeto en un archivo) o /DEF (para crear una biblioteca de importación).

Para crear una biblioteca a partir de objetos y/o bibliotecas, utilice la sintaxis siguiente:

```
LIB [options...] files...
```

Este comando crea una biblioteca a partir de uno o varios *archivos*de entrada. Los *archivos* pueden ser archivos de objetos COFF, archivos de objetos OMF de 32 bits o bibliotecas COFF existentes. LIB crea una biblioteca que contiene todos los objetos de los archivos especificados. Si un archivo de entrada es un archivo de objeto OMF de 32 bits, LIB lo convierte en COFF antes de crear la biblioteca. LIB no puede aceptar un objeto OMF de 32 bits que se encuentra en una biblioteca creada por la versión de 16 bits de LIB. Primero debe utilizar el LIB de 16 bits para extraer el objeto; a continuación, puede utilizar el archivo de objeto extraído como entrada para el LIB de 32 bits.

De forma predeterminada, LIB nombra el archivo de salida utilizando el nombre base del primer objeto o archivo de biblioteca y la extensión .lib. El archivo de salida se coloca en el directorio actual. Si ya existe un archivo con el mismo nombre, el archivo de salida reemplaza el archivo existente. Para conservar una biblioteca existente, utilice la opción /OUT para especificar un nombre para el archivo de salida.

Las siguientes opciones se aplican a la creación y modificación de una biblioteca:

**/LIBPATH:** *dir*<br/>
Reemplaza la ruta de acceso a la biblioteca de entorno. Para obtener más información, consulte la descripción de la opción LINK [/LIBPATH.](libpath-additional-libpath.md)

**/LISTA**<br/>
Muestra información sobre la biblioteca de salida en la salida estándar. La salida se puede redirigir a un archivo. Puede utilizar /LIST para determinar el contenido de una biblioteca existente sin modificarla.

**/NAME:** *nombre de archivo*<br/>
Al crear una biblioteca de importación, especifica el nombre del archivo DLL para el que se está compilando la biblioteca de importación.

**/NODEFAULTLIB**<br/>
Quita una o más bibliotecas predeterminadas de la lista de bibliotecas que busca al resolver referencias externas. Consulte [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) para obtener más información.

**/OUT:** *nombre de archivo*<br/>
Reemplaza el nombre de archivo de salida predeterminado. De forma predeterminada, la biblioteca de salida se crea en el directorio actual, con el nombre base de la primera biblioteca o archivo de objeto en la línea de comandos y la extensión .lib.

**/REMOVE:** *objeto*<br/>
Omite el *objeto* especificado de la biblioteca de salida. LIB crea una biblioteca de salida combinando todos los objetos (ya sea en archivos de objetoos o bibliotecas) y, a continuación, eliminando los objetos especificados con /REMOVE.

**/SUBSYSTEM:****CONSOLE** **&#124; EFI_APPLICATION** &#124; **&#124; EFI_BOOT_SERVICE_DRIVER** &#124; EFI_ROM EFI_ROM **&#124;** **EFI_RUNTIME_DRIVER** **&#124;** EFI_RUNTIME_DRIVER &#124; **WINDOWS** &#124; **WINDOWS** **&#124; WINDOWSCE**[,[.-]]<br/>
Indica al sistema operativo cómo ejecutar un programa creado mediante la vinculación a la biblioteca de salida. Para obtener más información, consulte la descripción de la opción LINK [/SUBSYSTEM.](subsystem-specify-subsystem.md)

Las opciones de LIB especificadas en la línea de comandos no distinguen entre mayúsculas y minúsculas.

Puede utilizar LIB para realizar las siguientes tareas de administración de bibliotecas:

- Para agregar objetos a una biblioteca, especifique el nombre de archivo de la biblioteca existente y los nombres de archivo de los nuevos objetos.

- Para combinar bibliotecas, especifique los nombres de archivo de biblioteca. Puede agregar objetos y combinar bibliotecas con un único comando LIB.

- Para reemplazar un miembro de biblioteca con un nuevo objeto, especifique la biblioteca que contiene el objeto miembro que se va a reemplazar y el nombre de archivo para el nuevo objeto (o la biblioteca que lo contiene). Cuando existe un objeto que tiene el mismo nombre en más de un archivo de entrada, LIB coloca el último objeto especificado en el mandato LIB en la biblioteca de salida. Cuando reemplace un miembro de biblioteca, asegúrese de especificar el nuevo objeto o biblioteca después de la biblioteca que contiene el objeto antiguo.

- Para eliminar un miembro de una biblioteca, utilice la opción /REMOVE. LIB procesa cualquier especificación de /REMOVE después de combinar todos los objetos de entrada, independientemente del orden de la línea de comandos.

> [!NOTE]
> No puede eliminar un miembro y extraerlo en un archivo en el mismo paso. Primero debe extraer el objeto miembro mediante /EXTRACT y, a continuación, ejecutar LIB de nuevo con /REMOVE. Este comportamiento difiere del de la LIB de 16 bits (para bibliotecas OMF) proporcionada en otros productos de Microsoft.

## <a name="see-also"></a>Consulte también

[Referencia de LIB](lib-reference.md)
