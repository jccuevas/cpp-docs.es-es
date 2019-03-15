---
title: Información general sobre LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 97d7b8892574fbe485a8d6c5e344e4a77aaf8519
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820226"
---
# <a name="overview-of-lib"></a>Información general sobre LIB

LIB crea bibliotecas estándar, bibliotecas de importación y exportación de archivos que puede usar con [vínculo](linker-options.md) al compilar un programa. LIB se ejecuta desde un símbolo del sistema.

Puede usar LIB en los siguientes modos:

- [Crear o modificar una biblioteca COFF](managing-a-library.md)

- [Extraer un objeto de miembro a un archivo](extracting-a-library-member.md)

- [Creación de un archivo de exportación y una biblioteca de importación](working-with-import-libraries-and-export-files.md)

Estos modos son mutuamente excluyentes; Puede usar LIB en modo de un solo a la vez.

## <a name="lib-options"></a>Opciones de lib

En la tabla siguiente se enumera las opciones de lib.exe, con un vínculo para obtener más información.

|Opción|Descripción|
|-|-|
|**/DEF**|Crear una biblioteca de importación y un archivo de exportación.<br/><br/>Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**|   Enviar información a Microsoft sobre errores internos de lib.exe.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|
|**/EXPORT**|   Exporta una función desde el programa.<br/><br/>Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Cree un archivo objeto (.obj) que contiene una copia de un miembro de una biblioteca existente.<br/><br/>Para obtener más información, consulte [extraer un miembro de biblioteca](extracting-a-library-member.md).|
|**/INCLUDE**|   Agrega un símbolo a la tabla de símbolos.<br/><br/>Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Reemplaza la ruta de acceso a la biblioteca de entorno.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/LIST**|   Muestra información acerca de la biblioteca de salida a la salida estándar.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/LTCG**|   Hace que la biblioteca que se crea mediante la generación de código en tiempo de vínculo.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|
|**/MACHINE**|   Especifica la plataforma de destino para el programa.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|
|**/NAME**|   Al compilar una biblioteca de importación, especifica el nombre del archivo DLL para el que se está compilando la biblioteca de importación.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/NODEFAULTLIB**|   Quita una o más bibliotecas predeterminadas de la lista de bibliotecas que realiza búsquedas al resolver referencias externas.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/NOLOGO**|   Suprime la presentación de la LIB copyright mensaje y número de versión e impide que un eco de los archivos de comandos.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|
|**/OUT**|   Invalida el nombre de archivo de salida predeterminado.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/REMOVE**|   Omite un objeto de la biblioteca de salida.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/SUBSYSTEM**|   Indica al sistema operativo cómo ejecutar un programa creado mediante la vinculación a la biblioteca de salida.<br/><br/>Para obtener más información, consulte [administrar una biblioteca](managing-a-library.md).|
|**/VERBOSE**|   Muestra los detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se va a agregar.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|
|**/WX**|   Tratar advertencias como errores.<br/><br/>Para obtener más información, consulte [ejecutar LIB](running-lib.md).|

## <a name="see-also"></a>Vea también

[Referencia de LIB](lib-reference.md)<br/>
[Archivos de entrada de LIB](lib-input-files.md)<br/>
[Archivos de resultados de LIB](lib-output-files.md)<br/>
[Otros resultados de LIB](other-lib-output.md)<br/>
[Estructura de una biblioteca](structure-of-a-library.md)
