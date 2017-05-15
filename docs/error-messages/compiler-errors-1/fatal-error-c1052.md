---
title: Error irrecuperable C1052 | Documentos de Microsoft
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1052
dev_langs:
- C++
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: 0
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: f3ab91c1c79b822a4d9a33fb0ab5fbd88146fff0
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="fatal-error-c1052"></a>Error irrecuperable C1052
archivo de base de datos de programa, '*filename*', se genera mediante el vinculador con/debug: Fastlink; compilador no puede actualizar estos archivos PDB; elimínela o use /Fd para especificar otro nombre de archivo PDB  
  
El compilador no puede actualizar los mismos archivos de base de datos (PDB) de programa que generan el vinculador cuando la [/Debug: Fastlink](../../build/reference/debug-generate-debug-info.md) se especifica la opción. Normalmente, los archivos PDB generado por el compilador y los archivos PDB generada por el vinculador tienen nombres diferentes. Sin embargo, si se configuran para utilizar los mismos nombres, puede producir este error.  
  
Para corregir este problema, puede eliminar explícitamente los archivos PDB antes de que compile de nuevo, o puede crear nombres diferentes para los archivos PDB generado por el compilador y generados por el enlazador. Para crear diferentes nombres de archivo PDB generado por el compilador en la línea de comandos, use el [/Fd](../../build/reference/fd-program-database-file-name.md) opción. Para generar nombres de archivo PDB diferentes en el IDE, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **C/C++**, **archivos de salida** , establezca el **nombre de archivo de base de datos de programa** propiedad. De forma predeterminada, esta propiedad es `$(IntDir)vc$(PlatformToolsetVersion).pdb`. Como alternativa, puede establecer el nombre del archivo PDB generada por el vinculador. Abra la **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **vinculador**, **depuración** , establezca el **generar archivo de base de datos de programa** propiedad. De manera predeterminada, esta propiedad está establecida en `$(OutDir)$(TargetName).pdb`.  

