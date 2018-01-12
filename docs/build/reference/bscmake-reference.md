---
title: Referencia de BSCMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0eeae72c2e7b3924c184f0e40e209986ad378809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-reference"></a>Referencia de BSCMAKE
> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.  
  
 La Utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE. (EXE) genera un archivo de información de examen (.bsc) a partir de archivos .sbr creados durante la compilación. Ciertas herramientas de terceros utilizan .bsc (archivos) para el análisis de código. 
  
 Al compilar el programa, puede crear un archivo de información de examen para el programa automáticamente, usando BSCMAKE para generar el archivo. No necesita saber cómo se ejecuta BSCMAKE si crea el archivo de información de examen en el entorno de desarrollo de Visual C++. Sin embargo, puede que desee leer este tema para comprender las opciones disponibles.  
  
 Si compila el programa fuera del entorno de desarrollo, aún puede crear un archivo .bsc personalizado que puede examinar en el entorno. Ejecute BSCMAKE en los archivos .sbr que creó durante la compilación.  
  
> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio Developer. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.  
  
 Esta sección contiene los siguientes temas:  
  
-   [Compilar archivos de información de examen: información general](../../build/reference/building-browse-information-files-overview.md)  
  
-   [Crear un archivo .bsc](../../build/reference/building-a-dot-bsc-file.md)  
  
-   [Línea de comandos BSCMAKE](../../build/reference/bscmake-command-line.md)  
  
-   [Archivo de comandos BSCMAKE](../../build/reference/bscmake-command-file-response-file.md)  
  
-   [Opciones de BSCMAKE](../../build/reference/bscmake-options.md)  
  
-   [Códigos de salida BSCMAKE](../../build/reference/bscmake-exit-codes.md)  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)