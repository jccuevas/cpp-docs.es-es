---
title: "Dos opciones para precompilar c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos)"
  - ".pch (archivos), precompilar opciones"
  - "precompilación automática"
  - "código, precompilar"
  - "compilar código fuente, precompilar"
  - "PCH (archivos)"
  - "PCH (archivos), precompilar opciones"
  - "archivos de encabezado precompilados"
  - "archivos de encabezado precompilados, precompilar opciones"
  - "precompilar código"
ms.assetid: f50ac76f-e2a2-462d-bda5-0e2ab7cccdeb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Dos opciones para precompilar c&#243;digo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Con Visual C\+\+, se puede precompilar cualquier código C o C\+\+, no sólo archivos de encabezado.  
  
 La precompilación requiere planificación, pero proporciona compilaciones mucho más rápidas si se precompila código fuente que no sea de archivos de encabezado sencillos.  
  
 Precompile código cuando sepa que los archivos de código fuente usan conjuntos de archivos de encabezado comunes, pero no los incluyen en el mismo orden, o cuando desee incluir código fuente en la precompilación.  
  
 Las opciones de encabezados precompilados son [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md) y [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md).  Utilice **\/Yc** para crear un encabezado precompilado.  Cuando se utiliza con el pragma opcional `hdrstop`, **\/Yc** permite precompilar tanto archivos de encabezado como de código fuente.  Seleccione **\/Yu** para utilizar un encabezado precompilado existente en la compilación activa.  También puede usar **\/Fp** con las opciones **\/Yc** e **\/Yu** para proporcionar un nombre alternativo para el encabezado precompilado.  
  
 Los temas de referencia de opciones del compilador para **\/Yu** e **\/Yc** tratan de cómo tener acceso a esta funcionalidad en el entorno de desarrollo.  
  
## Más información  
  
-   [Cuándo precompilar código fuente](../../build/reference/when-to-precompile-source-code.md)  
  
-   [Reglas de coherencia de los encabezados precompilados](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [Utilizar encabezados precompilados en un proyecto](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 Para obtener más ejemplos sobre el uso de encabezados precompilados, vea los archivos MAKE utilizados para compilar los programas de ejemplo que se suministran con la biblioteca de MFC \(Microsoft Foundation Class\).  
  
## Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)