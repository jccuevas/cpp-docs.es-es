---
title: Información general sobre LIB
description: Información general sobre el uso y las opciones de la herramienta biblioteca, lib. exe.
ms.date: 09/25/2019
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 7223ef0a624cf15c43bd067db8a7919efd27df17
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685489"
---
# <a name="overview-of-lib"></a>Información general sobre LIB

LIB (lib. exe) crea bibliotecas estándar, bibliotecas de importación y archivos de exportación que puede usar con el [vínculo](linker-options.md) al compilar un programa. LIB se ejecuta desde un símbolo del sistema.

Puede usar LIB en los modos siguientes:

- [Crear o modificar una biblioteca COFF](managing-a-library.md)

- [Extraer un objeto de miembro a un archivo](extracting-a-library-member.md)

- [Crear un archivo de exportación y una biblioteca de importación](working-with-import-libraries-and-export-files.md)

Estos modos son mutuamente excluyentes; puede usar LIB solo en un modo cada vez.

## <a name="lib-options"></a>Opciones de LIB

En la tabla siguiente se enumeran las opciones de lib. exe, con un vínculo a más información.

|Opción|Descripción|
|-|-|
|**/DEF**|Cree una biblioteca de importación y un archivo de exportación.<br/><br/>Para obtener más información, vea [crear una biblioteca de importación y un archivo de exportación](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**|   Enviar información a Microsoft acerca de los errores internos con lib. exe.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/EXPORT**|   Exporta una función desde el programa.<br/><br/>Para obtener más información, vea [crear una biblioteca de importación y un archivo de exportación](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Cree un archivo de objeto (. obj) que contenga una copia de un miembro de una biblioteca existente.<br/><br/>Para obtener más información, consulte [extraer un miembro de biblioteca](extracting-a-library-member.md).|
|**/INCLUDE**|   Agrega un símbolo a la tabla de símbolos.<br/><br/>Para obtener más información, vea [crear una biblioteca de importación y un archivo de exportación](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Reemplaza la ruta de acceso a la biblioteca de entorno.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/LINKREPRO**|   Crea artefactos necesarios para reproducir un bloqueo de lib. exe o un error interno.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/LINKREPROTARGET**|   Solo genera los artefactos de **/LINKREPRO** cuando se usa lib. exe con un archivo especificado.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/LIST**|   Muestra información sobre la biblioteca de salida en la salida estándar.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/LTCG**|   Hace que la biblioteca se compile mediante la generación de código en tiempo de vínculo.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/MACHINE**|   Especifica la plataforma de destino para el programa.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/NAME**|   Al compilar una biblioteca de importación, especifica el nombre del archivo DLL para el que se está compilando la biblioteca de importación.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/NODEFAULTLIB**|   Quita una o varias bibliotecas predeterminadas de la lista de bibliotecas en las que busca al resolver referencias externas.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/NOLOGO**|   Suprime la presentación del mensaje de copyright y el número de versión de LIB y evita que se repitan los archivos de comandos.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/OUT**|   Invalida el nombre de archivo de salida predeterminado.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/REMOVE**|   Omite un objeto de la biblioteca de salida.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/SUBSYSTEM**|   Indica al sistema operativo cómo ejecutar un programa creado mediante la vinculación a la biblioteca de salida.<br/><br/>Para obtener más información, consulte [Administración de una biblioteca](managing-a-library.md).|
|**/VERBOSE**|   Muestra detalles sobre el progreso de la sesión, incluidos los nombres de los archivos. obj que se van a agregar.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|
|**/WX**|   Trata las advertencias como errores.<br/><br/>Para más información, vea [Ejecutar LIB](running-lib.md).|

## <a name="see-also"></a>Vea también

[Referencia de LIB](lib-reference.md)<br/>
[Archivos de entrada de LIB](lib-input-files.md)<br/>
[Archivos de resultados de LIB](lib-output-files.md)<br/>
[Otros resultados de LIB](other-lib-output.md)<br/>
[Estructura de una biblioteca](structure-of-a-library.md)
