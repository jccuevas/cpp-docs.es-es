---
title: Archivos de encabezado precompilados
ms.date: 11/04/2016
f1_keywords:
- stdafx.h
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
ms.openlocfilehash: fed583464aa172887b80a8551adf86e02a76d210
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643214"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Estos archivos se usan para compilar un archivo de encabezado precompilado *Nombre_proyecto*.pch y un archivo de tipos precompilado Stdafx.obj.

Se encuentran en el directorio *Nombre_proyecto* . En el Explorador de soluciones, Stdafx.h está en la carpeta Header Files y Stdafx.cpp está en la carpeta Source Files.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|stdafx.h|Archivo de inclusión para archivos de inclusión del sistema estándar y para archivos de inclusión específicos del proyecto que se usen con frecuencia, pero que no suelan modificarse.<br /><br /> No debe definir ni anular la definición de ninguna de las macros _AFX_NO_XXX de stdafx.h.|
|stdafx.cpp|Contiene la directiva de preprocesador `#include "stdafx.h"` y agrega archivos de inclusión para tipos precompilados. Los archivos precompilados de cualquier tipo, incluidos los archivos de encabezado, ofrecen menor tiempo de compilación restringiendo la compilación únicamente a los archivos que la requieren. Después de compilar el proyecto por primera vez, observará que el tiempo de compilación es mucho menor en las compilaciones posteriores, gracias a la presencia de los archivos de encabezado precompilado.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)