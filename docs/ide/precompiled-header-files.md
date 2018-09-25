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
ms.openlocfilehash: 8d2e2bab9da3d19347577f0b1d1e8ab2ed6bb0dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404026"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Estos archivos se usan para compilar un archivo de encabezado precompilado *Nombre_proyecto*.pch y un archivo de tipos precompilado Stdafx.obj.

Se encuentran en el directorio *Nombre_proyecto* . En el Explorador de soluciones, Stdafx.h está en la carpeta Header Files y Stdafx.cpp está en la carpeta Source Files.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|stdafx.h|Archivo de inclusión para archivos de inclusión del sistema estándar y para archivos de inclusión específicos del proyecto que se usen con frecuencia, pero que no suelan modificarse.<br /><br /> No se debe definir ni eliminar la definición de ninguna de las macros _AFX_NO_XXX de stdafx.h. Consulte el artículo "PRB: Problems Occur When Defining _AFX_NO_XXX" de Knowledge Base. Encontrará artículos de Knowledge Base en los elementos multimedia de MSDN Library o en la dirección [http:// support.microsoft.com/](http://%20support.microsoft.com/).|
|stdafx.cpp|Contiene la directiva de preprocesador `#include "stdafx.h"` y agrega archivos de inclusión para tipos precompilados. Los archivos precompilados de cualquier tipo, incluidos los archivos de encabezado, ofrecen menor tiempo de compilación restringiendo la compilación únicamente a los archivos que la requieren. Después de compilar el proyecto por primera vez, observará que el tiempo de compilación es mucho menor en las compilaciones posteriores, gracias a la presencia de los archivos de encabezado precompilado.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)