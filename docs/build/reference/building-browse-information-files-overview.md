---
title: 'Generar archivos de información de examen: Información general'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 5d33460ba63e50d31e44384be382e98cfbea4c91
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220550"
---
# <a name="building-browse-information-files-overview"></a>Generar archivos de información de examen: Información general


> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Para crear información de examen para la exploración de símbolos, el compilador crea un archivo .sbr para cada archivo de código fuente en el proyecto, a continuación, BSCMAKE. EXE concatena los archivos .sbr en un archivo .bsc.

Generación de archivos .sbr y .bsc lleva tiempo, por lo que Visual Studio desactiva estas funciones de forma predeterminada. Si desea examinar la información actual, debe activar las opciones de exploración y compile el proyecto nuevo.

Use [/FR](fr-fr-create-dot-sbr-file.md) o [/Fr](fr-fr-create-dot-sbr-file.md) para indicar al compilador para crear los archivos. sbr. Para crear archivos .bsc, puede llamar a [BSCMAKE](bscmake-command-line.md) desde la línea de comandos. Uso de BSCMAKE desde la línea de comandos le ofrece control más preciso sobre la manipulación de archivos de información de examen. Consulte [referencia de BSCMAKE](bscmake-reference.md) para obtener más información.

> [!TIP]
>  Puede activar la generación de archivos .sbr pero dejar la generación del archivo .bsc ha desactivado. Esto proporciona generaciones rápidas, sino también le permite crear rápidamente un archivo .bsc nuevo activar la generación del archivo .bsc y compilar el proyecto.

Puede reducir el tiempo, memoria y espacio en disco necesario para crear un archivo .bsc reduciendo el tamaño del archivo .bsc.

Consulte [página de propiedades General (proyecto)](general-property-page-project.md) para obtener información sobre cómo crear un archivo de explorador en el entorno de desarrollo.

### <a name="to-create-a-smaller-bsc-file"></a>Para crear un archivo .bsc menor

1. Use [opciones de línea de comandos de BSCMAKE](bscmake-options.md) para excluir la información desde el archivo de información de examen.

1. Omitir símbolos locales en uno o más archivos .sbr al compilar o ensamblar.

1. Si un archivo objeto no contiene información necesaria para la fase actual de la depuración, omita su archivo .sbr del comando BSCMAKE cuando vuelve a generar el archivo de información de examen.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Para combinar la información de examen de varios proyectos en un archivo del explorador (.bsc)

1. No generar el archivo .bsc en el nivel de proyecto o usar el modificador /n para impedir que los archivos .sbr que se va a truncar.

1. Después de que todos los proyectos se compilan, ejecute BSCMAKE con todos los archivos .sbr como entrada. Se aceptan caracteres comodín. Por ejemplo, si tenía directorios de proyecto C:\X, C:\Y y C:\Z con los archivos .sbr en ellos y desea combinar todos ellos en un archivo .bsc, a continuación, use BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*.sbr /o c:\whatever_directory\combined.bsc para generar el archivo .bsc combinado.

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](c-cpp-build-tools.md)<br/>
[Referencia de BSCMAKE](bscmake-reference.md)
