---
title: 'Compilar archivos de información de examen: información general'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320671"
---
# <a name="building-browse-information-files-overview"></a>Compilar archivos de información de examen: información general

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Para crear información de exploración para la exploración de símbolos, el compilador crea un archivo .sbr para cada archivo de origen del proyecto y, a continuación, BSCMAKE. EXE concatena los archivos .sbr en un archivo .bsc.

La generación de archivos .sbr y .bsc lleva tiempo, por lo que Visual Studio desactiva estas funciones de forma predeterminada. Si desea examinar la información actual, debe activar las opciones de exploración y compilar el proyecto de nuevo.

Utilice [/FR](fr-fr-create-dot-sbr-file.md) o [/Fr](fr-fr-create-dot-sbr-file.md) para indicar al compilador que cree archivos .sbr. Para crear archivos .bsc, puede llamar a [BSCMAKE](bscmake-command-line.md) desde la línea de comandos. El uso de BSCMAKE desde la línea de comandos le proporciona un control más preciso sobre la manipulación de los archivos de información de exploración. Consulte [Referencia de BSCMAKE](bscmake-reference.md) para obtener más información.

> [!TIP]
> Puede activar la generación de archivos .sbr pero dejar desactivada la generación de archivos .bsc. Esto proporciona compilaciones rápidas, pero también le permite crear un archivo .bsc nuevo rápidamente activando la generación de archivos .bsc y compilando el proyecto.

Puede reducir el tiempo, la memoria y el espacio en disco necesarios para crear un archivo .bsc reduciendo el tamaño del archivo .bsc.

Consulte Página de propiedades [generales (proyecto)](general-property-page-project.md) para obtener información sobre cómo crear un archivo de explorador en el entorno de desarrollo.

### <a name="to-create-a-smaller-bsc-file"></a>Para crear un archivo .bsc más pequeño

1. Utilice las [opciones de línea de comandos](bscmake-options.md) de BSCMAKE para excluir información del archivo de información de exploración.

1. Omita los símbolos locales en uno o varios archivos .sbr al compilar o ensamblar.

1. Si un archivo de objeto no contiene la información necesaria para la fase actual de depuración, omita su archivo .sbr del comando BSCMAKE al volver a generar el archivo de información de exploración.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Para combinar la información de exploración de varios proyectos en un archivo de explorador (.bsc)

1. No compile el archivo .bsc en el nivel de proyecto o use el modificador /n para evitar que los archivos .sbr se trunquen.

1. Después de compilar todos los proyectos, ejecute BSCMAKE con todos los archivos .sbr como entrada. Se aceptan caracteres comodín. Por ejemplo, si tenía directorios de proyecto C:-X, C:-Y y C:-Z con archivos .sbr en ellos y deseaba combinarlos todos en un\\\*archivo .bsc,\\\*a continuación, utilice BSCMAKE C:-X\\\*.sbr C:-Y .sbr C:-Z .sbr /o c:-whatever_directory-combined.bsc para construir el archivo .bsc combinado.

## <a name="see-also"></a>Consulte también

[Herramientas de compilación de MSVC adicionales](c-cpp-build-tools.md)<br/>
[Referencia de BSCMAKE](bscmake-reference.md)
