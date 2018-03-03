---
title: "Información general sobre LIB | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef3d1e57371fdea62bb557830baca633f4165637
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-lib"></a>Información general sobre LIB
LIB crea bibliotecas estándar, bibliotecas de importación y exportación de archivos se pueden usar con [vínculo](../../build/reference/linker-options.md) al compilar un programa. LIB se ejecuta desde un símbolo del sistema.  
  
 Puede usar LIB en los siguientes modos:  
  
-   [Crear o modificar una biblioteca COFF](../../build/reference/managing-a-library.md)  
  
-   [Extraer un objeto de miembro a un archivo](../../build/reference/extracting-a-library-member.md)  
  
-   [Crear un archivo de exportación y una biblioteca de importación](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 Estos modos son mutuamente excluyentes; Puede usar LIB en solo modo a la vez.  
  
## <a name="lib-options"></a>Opciones de lib  
 En la tabla siguiente se enumera las opciones de lib.exe, con un vínculo para obtener más información.  
  
 **/ DEF**  
 Crear una biblioteca de importación y un archivo de exportación.  
  
 Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ ERRORREPORT**  
 Enviar información a Microsoft sobre errores internos de lib.exe.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
 **/ EXPORTACIÓN**  
 Exporta una función desde el programa.  
  
 Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ EXTRACT**  
 Cree un archivo objeto (.obj) que contiene una copia de un miembro de una biblioteca existente.  
  
 Para obtener más información, consulte [extraer un miembro de biblioteca](../../build/reference/extracting-a-library-member.md).  
  
 **/ INCLUYEN**  
 Agrega un símbolo a la tabla de símbolos.  
  
 Para obtener más información, consulte [crear bibliotecas de importación y exportación de archivo](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **/ LIBPATH**  
 Reemplaza la ruta de acceso a la biblioteca de entorno.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ LISTA**  
 Muestra información acerca de la biblioteca de salida a la salida estándar.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ LTCG**  
 Hace que la biblioteca que se crea utilizando la generación de código en tiempo de vínculo.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
 **/ MÁQUINA**  
 Especifica la plataforma de destino para el programa.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
 **/ NAME**  
 Cuando se crea una biblioteca de importación, especifica el nombre del archivo DLL para el que se está generando la biblioteca de importación.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ NODEFAULTLIB**  
 Quita una o más bibliotecas predeterminadas de la lista de bibliotecas que se busca al resolver referencias externas.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ NOLOGO**  
 Suprime la presentación de la LIB copyright mensaje y número de versión e impide el eco de los archivos de comandos.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
 **/ ENTRADA SALIDA**  
 Invalida el nombre de archivo de salida predeterminado.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **O QUITAR**  
 Omite un objeto de la biblioteca de salida.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ SUBSISTEMA**  
 Indica al sistema operativo cómo ejecutar un programa creado mediante la vinculación a la biblioteca de salida.  
  
 Para obtener más información, consulte [administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **/ DETALLADO**  
 Muestra los detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se va a agregar.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
 **/WX**  
 Tratar advertencias como errores.  
  
 Para obtener más información, consulte [ejecutar LIB](../../build/reference/running-lib.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)   
 [Archivos de entrada de LIB](../../build/reference/lib-input-files.md)   
 [Archivos de resultados LIB](../../build/reference/lib-output-files.md)   
 [Otros resultados de LIB](../../build/reference/other-lib-output.md)   
 [Estructura de una biblioteca](../../build/reference/structure-of-a-library.md)