---
title: Error irrecuperable C1052 | Documentos de Microsoft
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1052
dev_langs: C++
helpviewer_keywords: C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a64caf82dcc99a26d7eb46d6e27465b0a8976edb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1052"></a>Error irrecuperable C1052  
  
> archivo de base de datos de programa, '*filename*', se genera mediante el vinculador con/debug: Fastlink; compilador no puede actualizar estos archivos PDB; elimínela o use /Fd para especificar otro nombre de archivo PDB  
  
El compilador no puede actualizar los mismos archivos de base de datos (PDB) de programa que generan el vinculador cuando la [/Debug: Fastlink](../../build/reference/debug-generate-debug-info.md) se especifica la opción. Normalmente, los archivos PDB generado por el compilador y los archivos PDB generada por el vinculador tienen nombres diferentes. Sin embargo, si se configuran para utilizar los mismos nombres, puede producir este error.  
  
Para corregir este problema, puede eliminar explícitamente los archivos PDB antes de que compile de nuevo, o puede crear nombres diferentes para los archivos PDB generado por el compilador y generados por el enlazador.  
  
Para especificar el nombre del archivo PDB generado por el compilador en la línea de comandos, utilice la [/Fd](../../build/reference/fd-program-database-file-name.md) opción del compilador. Para especificar el nombre del archivo PDB generado por el compilador en el IDE, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **C/C++**,  **Archivos de salida** , establezca el **nombre de archivo de base de datos de programa** propiedad. De forma predeterminada, esta propiedad es `$(IntDir)vc$(PlatformToolsetVersion).pdb`.  
  
Como alternativa, puede establecer el nombre del archivo PDB generada por el vinculador. Para especificar el nombre del archivo PDB generados por el enlazador en la línea de comandos, utilice la [/PDB](../../build/reference/pdb-use-program-database.md) opción del vinculador. Para especificar el nombre del archivo PDB generada por el vinculador en el IDE, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **vinculador**,  **Depuración** , establezca el **generar archivo de base de datos de programa** propiedad. De manera predeterminada, esta propiedad está establecida en `$(OutDir)$(TargetName).pdb`.  
