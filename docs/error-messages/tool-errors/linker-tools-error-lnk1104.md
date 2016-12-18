---
title: "Error de las herramientas del vinculador LNK1104 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1104"
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir el archivo 'file'  
  
 La herramienta no pudo abrir el archivo especificado.  
  
 Posibles causas del error:  
  
-   No hay suficiente espacio en el disco.  
  
-   No existe el archivo.  
  
-   Al especificar bibliotecas en el cuadro de diálogo de páginas de propiedades de un proyecto, los nombres de biblioteca deben estar separados por espacios \(y no por comas\).  
  
-   Nombre de archivo o ruta de acceso incorrectos.  
  
-   Especificación de unidad no válida.  
  
-   Permisos de archivo insuficientes.  
  
-   La ruta de acceso de `filename` se expande a más de 260 caracteres.  
  
-   Si el archivo dado se denomina `LNKn`, que es un nombre de archivo generado por el enlazador para un archivo temporal, es posible que no exista el directorio especificado en la variable de entorno de TMP o que se hay especificado más de un directorio en la variable de entorno de TMP. \(Solo se debe especificar una ruta de acceso de directorio en la variable de entorno de TMP\).  
  
-   Si el mensaje de error se produce para un nombre de biblioteca, y se portó recientemente el archivo .mak de un sistema de desarrollo de Microsoft Visual C\+\+ anterior, es posible que la biblioteca ya no sea válida. Asegúrese de que la biblioteca todavía existe en esta circunstancia.  
  
-   Puede que otro programa tenga el archivo abierto y que el enlazador no puede escribir en él.  
  
-   Variable de entorno de LIB incorrecta. Para información sobre cómo actualizar la variable de entorno de LIB, vea [Directorios de VC\+\+ \(Página de propiedades\)](../../ide/vcpp-directories-property-page.md). Asegúrese de que los directorios que contienen las bibliotecas que necesita aparecen aquí.  
  
 El enlazador usa archivos temporales en varios casos. Aunque tenga espacio en disco suficiente, un vínculo muy grande puede disminuir o fragmentar el espacio de direcciones.  
  
 Para corregir mediante las siguientes posibles soluciones  
  
-   Use [\/OPT \(Optimizaciones\)](../../build/reference/opt-optimizations.md); al realizar la eliminación de comdat transitiva se leen todos los archivos de objeto varias veces.  
  
-   Actualización a Windows XP.