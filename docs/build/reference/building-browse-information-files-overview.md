---
title: 'Generar archivos de información de examen: Información general sobre | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2306c69c219320e11259ba6303b76588db8f7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="building-browse-information-files-overview"></a>Compilar archivos de información de examen: información general
Para crear información de exploración para la exploración de símbolos, el compilador crea un archivo .sbr para cada archivo de código fuente en el proyecto, a continuación, BSCMAKE. EXE concatena los archivos .sbr en un archivo .bsc.  
  
 Generar archivos .sbr y .bsc lleva tiempo, por lo que Visual C++ desactiva estas funciones de forma predeterminada. Si desea buscar la información actual, debe activar las opciones de exploración y compilar el proyecto de nuevo.  
  
 Use [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) o [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) para indicar al compilador que crean archivos. sbr. Para crear archivos .bsc, puede llamar a [BSCMAKE](../../build/reference/bscmake-command-line.md) desde la línea de comandos. Uso de BSCMAKE desde la línea de comandos proporciona un control más preciso sobre la manipulación de archivos de información de exploración. Vea [referencia de BSCMAKE](../../build/reference/bscmake-reference.md) para obtener más información.  
  
> [!TIP]
>  Puede activar la generación de archivos .sbr pero dejar la generación del archivo .bsc está desactivada. Esto proporciona generaciones rápidas, sino también le permite crear rápidamente un archivo .bsc nuevo por activar la generación de archivos .bsc y generando el proyecto.  
  
 Puede reducir el tiempo, memoria y espacio en disco necesario para generar un archivo .bsc reduciendo el tamaño del archivo .bsc.  
  
 Vea [página de propiedades General (proyecto)](../../ide/general-property-page-project.md) para obtener información sobre cómo crear un archivo de explorador en el entorno de desarrollo.  
  
### <a name="to-create-a-smaller-bsc-file"></a>Para crear un archivo .bsc más pequeño  
  
1.  Use [opciones de línea de comandos de BSCMAKE](../../build/reference/bscmake-options.md) para excluir la información desde el archivo de información de examen.  
  
2.  Omita los símbolos locales en uno o más archivos .sbr al compilar o ensamblar.  
  
3.  Si un archivo de objeto no contiene la información necesaria para la fase actual de la depuración, omita su archivo .sbr del comando BSCMAKE cuando se vuelve a generar el archivo de información de examen.  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Para combinar la información de examen de varios proyectos en un archivo del explorador (.bsc)  
  
1.  No generar el archivo .bsc en el nivel de proyecto o usar el modificador /n para impedir que los archivos .sbr que se va a truncar.  
  
2.  Después de que se generan todos los proyectos, ejecute BSCMAKE con todos los archivos .sbr como entrada. Se acepta caracteres comodín. Por ejemplo, si tenía directorios del proyecto C:\X, C:\Y y C:\Z con archivos .sbr en ellos y se desea combinar todos ellos en un archivo .bsc, utilice BSCMAKE C:\X\\*.sbr C:\Y\\\*.sbr C:\Z\\\*. SBR /o c:\whatever_directory\combined.bsc para generar el archivo .bsc combinado.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de compilación de C/c ++](../../build/reference/c-cpp-build-tools.md)   
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)