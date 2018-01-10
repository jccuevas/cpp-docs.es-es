---
title: Resultados de LINK | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 567a87ab5cb4badd5f32423b8fb3067b21c46e9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="link-output"></a>Resultados de LINK
Resultados de LINK incluyen archivos .exe, DLL, archivos de asignaciones y mensajes.  
  
##  <a name="_core_output_files"></a>Archivos de salida  
 El archivo de salida predeterminado de LINK es un archivo .exe. Si el [/DLL](../../build/reference/dll-build-a-dll.md) , LINK generará un archivo DLL. Puede controlar el nombre de archivo de salida con el [nombre de archivo de salida (/ OUT)](../../build/reference/out-output-file-name.md) opción.  
  
 En el modo incremental, LINK crea un archivo .ilk que contiene información de estado para posteriores generaciones incrementales del programa. Para obtener más información sobre los archivos .ilk, vea [archivos .ilk](../../build/reference/dot-ilk-files-as-linker-input.md). Para obtener más información sobre la vinculación incremental, vea la [vínculo incremental (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opción.  
  
 Cuando LINK crea un programa que contiene exportaciones (normalmente un archivo DLL), crea también un archivo .lib, a menos que se utilice un archivo .exp en la compilación. Puede controlar el nombre de archivo de biblioteca de importación con la [/IMPLIB](../../build/reference/implib-name-import-library.md) opción.  
  
 Si el [generar archivo de asignaciones (/ MAP)](../../build/reference/map-generate-mapfile.md) , LINK creará un archivo de asignaciones.  
  
 Si el [generar información de depuración (/Debug)](../../build/reference/debug-generate-debug-info.md) , LINK creará una PDB para contener la información de depuración para el programa.  
  
##  <a name="_core_other_output"></a>Otros resultados  
 Cuando escriba `link` sin ninguna entrada de línea de comandos, LINK muestra una instrucción de uso que se resume sus opciones.  
  
 VÍNCULO muestra un mensaje de copyright y la versión y repetir la entrada, en el archivo de comandos, a menos que la [suprimir el titular de inicio (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md) se utiliza la opción.  
  
 Puede usar el [imprimir mensajes de progreso (/ VERBOSE)](../../build/reference/verbose-print-progress-messages.md) opción para mostrar detalles adicionales acerca de la compilación.  
  
 LINK emite los mensajes de error y advertencia en el formato LNK*nnnn*. También se utilizan el prefijo de error y el intervalo de números de LIB, DUMPBIN y EDITBIN.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)