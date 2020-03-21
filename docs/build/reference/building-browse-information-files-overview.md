---
title: 'Compilar archivos de información de examen: información general'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078361"
---
# <a name="building-browse-information-files-overview"></a>Compilar archivos de información de examen: información general

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Para crear información de examen para la exploración de símbolos, el compilador crea un archivo. SBR para cada archivo de código fuente del proyecto y, a continuación, BSCMAKE. EXE concatena los archivos. SBR en un archivo. BSC.

La generación de archivos. SBR y. BSC lleva tiempo, por lo que Visual Studio desactiva estas funciones de forma predeterminada. Si desea examinar la información actual, debe activar las opciones de exploración y compilar el proyecto de nuevo.

Utilice [/fr](fr-fr-create-dot-sbr-file.md) o [/fr](fr-fr-create-dot-sbr-file.md) para indicar al compilador que cree archivos. SBR. Para crear archivos. BSC, puede llamar a [BSCMAKE](bscmake-command-line.md) desde la línea de comandos. El uso de BSCMAKE desde la línea de comandos proporciona un control más preciso sobre la manipulación de los archivos de información de examen. Vea [referencia de BSCMAKE](bscmake-reference.md) para obtener más información.

> [!TIP]
>  Puede activar la generación de archivos. SBR pero dejar la generación de archivos. BSC desactivada. Esto proporciona compilaciones rápidas, pero también permite crear un archivo. BSC nuevo rápidamente activando la generación de archivos. BSC y compilando el proyecto.

Puede reducir el tiempo, la memoria y el espacio en disco necesarios para generar un archivo. BSC reduciendo el tamaño del archivo. BSC.

Vea [Página de propiedades general (proyecto)](general-property-page-project.md) para obtener información sobre cómo compilar un archivo de explorador en el entorno de desarrollo.

### <a name="to-create-a-smaller-bsc-file"></a>Para crear un archivo. BSC más pequeño

1. Use [las opciones de línea de comandos de BSCMAKE](bscmake-options.md) para excluir información del archivo de información de examen.

1. Omitir símbolos locales en uno o varios archivos. SBR al compilar o ensamblar.

1. Si un archivo objeto no contiene la información necesaria para la fase de depuración actual, omita el archivo. SBR del comando BSCMAKE al volver a generar el archivo de información de examen.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Para combinar la información de examen de varios proyectos en un archivo de explorador (. BSC)

1. No compile el archivo. BSC en el nivel de proyecto o use el modificador/n para evitar que se trunquen los archivos. SBR.

1. Después de compilar todos los proyectos, ejecute BSCMAKE con todos los archivos. SBR como entrada. Se aceptan caracteres comodín. Por ejemplo, si tiene directorios de proyecto C:\X, C:\Y y C:\Z con archivos. SBR y desea combinarlos en un archivo. BSC, use BSCMAKE C:\X\\\*. SBR C:\Y\\\*. SBR C:\Z\\\*. SBR/o c:\ whatever_directory \combined.BSC para compilar el archivo. BSC combinado.

## <a name="see-also"></a>Consulte también

[Herramientas de compilación de MSVC adicionales](c-cpp-build-tools.md)<br/>
[Referencia de BSCMAKE](bscmake-reference.md)
