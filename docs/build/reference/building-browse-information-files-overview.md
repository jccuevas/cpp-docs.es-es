---
title: 'Compilar archivos de información de examen: información general'
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: d620c7170ef5e84a05496af6e74d3a22f594749b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469983"
---
# <a name="building-browse-information-files-overview"></a>Compilar archivos de información de examen: información general

Para crear información de examen para la exploración de símbolos, el compilador crea un archivo .sbr para cada archivo de código fuente en el proyecto, a continuación, BSCMAKE. EXE concatena los archivos .sbr en un archivo .bsc.

Generación de archivos .sbr y .bsc lleva tiempo, por lo que Visual C++ desactiva estas funciones de forma predeterminada. Si desea examinar la información actual, debe activar las opciones de exploración y compile el proyecto nuevo.

Use [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) o [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) para indicar al compilador para crear los archivos. sbr. Para crear archivos .bsc, puede llamar a [BSCMAKE](../../build/reference/bscmake-command-line.md) desde la línea de comandos. Uso de BSCMAKE desde la línea de comandos le ofrece control más preciso sobre la manipulación de archivos de información de examen. Consulte [referencia de BSCMAKE](../../build/reference/bscmake-reference.md) para obtener más información.

> [!TIP]
>  Puede activar la generación de archivos .sbr pero dejar la generación del archivo .bsc ha desactivado. Esto proporciona generaciones rápidas, sino también le permite crear rápidamente un archivo .bsc nuevo activar la generación del archivo .bsc y compilar el proyecto.

Puede reducir el tiempo, memoria y espacio en disco necesario para crear un archivo .bsc reduciendo el tamaño del archivo .bsc.

Consulte [página de propiedades General (proyecto)](../../ide/general-property-page-project.md) para obtener información sobre cómo crear un archivo de explorador en el entorno de desarrollo.

### <a name="to-create-a-smaller-bsc-file"></a>Para crear un archivo .bsc menor

1. Use [opciones de línea de comandos de BSCMAKE](../../build/reference/bscmake-options.md) para excluir la información desde el archivo de información de examen.

1. Omitir símbolos locales en uno o más archivos .sbr al compilar o ensamblar.

1. Si un archivo objeto no contiene información necesaria para la fase actual de la depuración, omita su archivo .sbr del comando BSCMAKE cuando vuelve a generar el archivo de información de examen.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Para combinar la información de examen de varios proyectos en un archivo del explorador (.bsc)

1. No generar el archivo .bsc en el nivel de proyecto o usar el modificador /n para impedir que los archivos .sbr que se va a truncar.

1. Después de que todos los proyectos se compilan, ejecute BSCMAKE con todos los archivos .sbr como entrada. Se aceptan caracteres comodín. Por ejemplo, si tenía directorios de proyecto C:\X, C:\Y y C:\Z con los archivos .sbr en ellos y desea combinar todos ellos en un archivo .bsc, a continuación, use BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*.sbr /o c:\whatever_directory\combined.bsc para generar el archivo .bsc combinado.

## <a name="see-also"></a>Vea también

[Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)
