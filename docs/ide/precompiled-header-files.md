---
title: "Archivos de encabezado precompilados | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""stdafx.h""
  - "stdafx.h"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stdafx.h"
  - "archivos PCH, descripciones de archivo"
  - "archivos .pch, descripciones de archivo"
  - "archivos de encabezado precompilado, descripciones de archivo"
  - "stdafx.cpp"
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de encabezado precompilados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estos archivos se usan para compilar un archivo de encabezado precompilado *Nombre\_proyecto*.pch y un archivo de tipos precompilado Stdafx.obj.  
  
 Se encuentran en el directorio *Nombre\_proyecto*. En el Explorador de soluciones, Stdafx.h está en la carpeta Header Files y Stdafx.cpp está en la carpeta Source Files.  
  
|Nombre del archivo|Descripción|  
|------------------------|-----------------|  
|Stdafx.h|Archivo de inclusión para archivos de inclusión del sistema estándar y para archivos de inclusión específicos del proyecto que se usen con frecuencia, pero que no suelan modificarse.<br /><br /> No se debe definir ni eliminar la definición de ninguna de las macros \_AFX\_NO\_XXX de stdafx.h. Consulte el artículo "PRB: Problems Occur When Defining \_AFX\_NO\_XXX" de Knowledge Base. Encontrará artículos de Knowledge Base en los elementos multimedia de MSDN Library o en la dirección [http:\/\/ support.microsoft.com\/](http://%20support.microsoft.com/).|  
|Stdafx.cpp|Contiene la directiva de preprocesador `#include "stdafx.h"` y agrega archivos de inclusión para tipos precompilados. Los archivos precompilados de cualquier tipo, incluidos los archivos de encabezado, ofrecen menor tiempo de compilación restringiendo la compilación únicamente a los archivos que la requieren. Después de compilar el proyecto por primera vez, observará que el tiempo de compilación es mucho menor en las compilaciones posteriores, gracias a la presencia de los archivos de encabezado precompilado.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Cómo: Especificar propiedades de proyecto con páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md)