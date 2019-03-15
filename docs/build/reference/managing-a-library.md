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
ms.openlocfilehash: 74b8cf198d46f83de327c68ac5f883bd75e5db80
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812049"
---
# <a name="managing-a-library"></a>Administrar una biblioteca

Es el modo predeterminado de LIB crear o modificar una biblioteca de objetos COFF. LIB se ejecuta en este modo, cuando no se especifica/Extract (para copiar un objeto en un archivo) o /DEF (para crear una biblioteca de importación).

Para generar una biblioteca de objetos o bibliotecas, use la sintaxis siguiente:

```
LIB [options...] files...
```

Este comando crea una biblioteca de la entrada de uno o varios *archivos*. El *archivos* pueden ser archivos objeto COFF, archivos de objeto OMF de 32 bits o bibliotecas COFF existentes. LIB crea una biblioteca que contiene todos los objetos en los archivos especificados. Si un archivo de entrada es un archivo de objeto OMF de 32 bits, LIB lo convierte a COFF antes de compilar la biblioteca. LIB no puede aceptar un objeto OMF de 32 bits que se encuentra en una biblioteca creada por la versión de 16 bits de LIB. En primer lugar, debe usar la biblioteca de 16 bits para extraer el objeto; a continuación, puede usar el archivo objeto extraído como entrada de LIB de 32 bits.

De forma predeterminada, el archivo de salida con el nombre base del primer archivo de biblioteca u objeto y la extensión de los nombres de LIB. lib. El archivo de salida se coloca en el directorio actual. Si ya existe un archivo con el mismo nombre, el archivo de salida reemplaza el archivo existente. Para mantener una biblioteca existente, utilice la opción /OUT para especificar un nombre para el archivo de salida.

Las siguientes opciones se aplican a la creación y modificación de una biblioteca:

**/LIBPATH:** *dir*<br/>
Reemplaza la ruta de acceso a la biblioteca de entorno. Para obtener más información, vea la descripción del vínculo [/libpath](libpath-additional-libpath.md) opción.

**/LIST**<br/>
Muestra información acerca de la biblioteca de salida a la salida estándar. La salida se puede redirigir a un archivo. Puede usar /LIST para determinar el contenido de una biblioteca existente sin modificarlo.

**/ NAME:** *nombre de archivo*<br/>
Al compilar una biblioteca de importación, especifica el nombre del archivo DLL para el que se está compilando la biblioteca de importación.

**/NODEFAULTLIB**<br/>
Quita una o más bibliotecas predeterminadas de la lista de bibliotecas que realiza búsquedas al resolver referencias externas. Consulte [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) para obtener más información.

**/ OUT:** *nombre de archivo*<br/>
Invalida el nombre de archivo de salida predeterminado. De forma predeterminada, se crea la biblioteca de salida en el directorio actual, con el nombre base del primer archivo objeto o biblioteca en la línea de comandos y la extensión. lib.

**/ REMOVE:** *objeto*<br/>
Omite especificado *objeto* desde la biblioteca de salida. LIB crea una biblioteca de salida combinando todos los objetos (en archivos objeto o bibliotecas) y, a continuación, elimina los objetos especificados con/Remove.

**/ SUBSYSTEM:**{**CONSOLA** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM** &AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **NATIVO** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [, #[. ##]]<br/>
Indica al sistema operativo cómo ejecutar un programa creado mediante la vinculación a la biblioteca de salida. Para obtener más información, vea la descripción del vínculo [/Subsystem](subsystem-specify-subsystem.md) opción.

Opciones de LIB especificadas en la línea de comandos no distinguen mayúsculas de minúsculas.

Puede utilizar LIB para realizar las siguientes tareas de administración de bibliotecas:

- Para agregar objetos a una biblioteca, especifique el nombre de archivo para la biblioteca existente y los nombres de archivo para los nuevos objetos.

- Para combinar las bibliotecas, especifique los nombres de archivo de biblioteca. Puede agregar objetos y combinar bibliotecas con un solo comando LIB.

- Para reemplazar a un miembro de biblioteca con un nuevo objeto, especifique el nombre de archivo para el nuevo objeto (o la biblioteca que lo contiene) y de la biblioteca que contiene el objeto de miembro que se debe reemplazar. Cuando existe un objeto que tiene el mismo nombre en más de un archivo de entrada, LIB coloca el último objeto especificado en el comando LIB en la biblioteca de salida. Al reemplazar un miembro de biblioteca, asegúrese de especificar el nuevo objeto o biblioteca después de la biblioteca que contiene el objeto antiguo.

- Para eliminar a un miembro de una biblioteca, use la opción/Remove. LIB procesa las especificaciones de /REMOVE después de combinar todos los objetos de entrada, independientemente del criterio de línea de comandos.

> [!NOTE]
>  No puede eliminar a un miembro y extráigalo en un archivo en el mismo paso. En primer lugar, debe extraer el objeto miembro mediante/Extract y luego ejecutar LIB nuevo con/Remove. Este comportamiento difiere de la biblioteca de 16 bits (para las bibliotecas OMF) proporcionada en otros productos de Microsoft.

## <a name="see-also"></a>Vea también

[Referencia de LIB](lib-reference.md)
