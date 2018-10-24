---
title: Archivos de encabezado precompilados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- stdafx.h
dev_langs:
- C++
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d93486d8df8cdb8bc253a0e71037f4e2ddf9e128
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890484"
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