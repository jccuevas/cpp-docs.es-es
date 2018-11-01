---
title: Error irrecuperable C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479773"
---
# <a name="fatal-error-c1052"></a>Error irrecuperable C1052

> archivo de base de datos de programa, '*filename*', fue generado por el vinculador con/debug: Fastlink; compilador no puede actualizar estos archivos PDB; elimínelo o utilice /Fd para especificar otro nombre de archivo PDB

El compilador no puede actualizar los mismos archivos de base de datos (PDB) de programa que generan el vinculador cuando la [/Debug: Fastlink](../../build/reference/debug-generate-debug-info.md) se especifica la opción. Normalmente, los archivos PDB generado por el compilador y los archivos PDB generada por el vinculador tienen nombres diferentes. Sin embargo, si están establecidos para usar los mismos nombres, puede provocar este error.

Para corregir este problema, puede eliminar explícitamente los archivos PDB antes de que vuelva a compilar, o bien puede crear nombres diferentes para los archivos PDB generado por el compilador y vinculador generado.

Para especificar el nombre del archivo PDB generado por el compilador en la línea de comandos, use el [/Fd](../../build/reference/fd-program-database-file-name.md) opción del compilador. Para especificar el nombre del archivo PDB generado por el compilador en el IDE, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **C o C++**,  **Los archivos de salida** , establezca el **nombre del archivo de base de datos de programa** propiedad. De forma predeterminada, esta propiedad es `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Como alternativa, puede establecer el nombre del archivo PDB generado por el vinculador. Para especificar el nombre del archivo PDB generado por el enlazador en la línea de comandos, use el [/PDB](../../build/reference/pdb-use-program-database.md) opción del vinculador. Para especificar el nombre del archivo PDB generado por el vinculador en el IDE, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **propiedades de configuración**, **vinculador**,  **Depuración** , establezca el **generar archivo de base de datos de programa** propiedad. De manera predeterminada, esta propiedad está establecida en `$(OutDir)$(TargetName).pdb`.
