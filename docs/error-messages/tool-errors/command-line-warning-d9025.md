---
title: "Advertencia de la l&#237;nea de comandos D9025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9025"
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de la l&#237;nea de comandos D9025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

reemplazando 'opción1' con 'opción2'  
  
 Se especificó la opción *opción1* pero, a continuación, se reemplazó por la *opción2*.  Se ha utilizado la opción *opción2*.  
  
 Si dos opciones especifican directivas contradictorias o incompatibles, se utiliza la directiva especificada o implementada en la opción más a la derecha en la línea de comandos.  
  
 Si aparece esta advertencia durante una compilación desde el entorno de desarrollo y no sabe de dónde proceden las opciones incompatibles, considere lo siguiente:  
  
-   Una opción se puede especificar en código o en la configuración del proyecto.  Si consulta las [páginas de propiedades de línea de comandos](../../ide/command-line-property-pages.md) del compilador y si ve las opciones incompatibles en el campo **Todas las opciones**, significa que las opciones se han establecido en las páginas de propiedades del proyecto. De no ser así, las opciones se establecieron en código fuente.  
  
     Si las opciones se han establecido en las páginas de propiedades del proyecto, consulte la página de propiedades Preprocesador del compilador \(con el nodo de proyecto seleccionado en el Explorador de soluciones\).  Si no ve la opción definida allí, revise las opciones de la página de propiedades Preprocesador para cada archivo de código fuente \(en el Explorador de soluciones\), para asegurarse de que no se ha agregado allí.  
  
     Si las opciones se han establecido en código, puede haber sido en código o en los encabezados de ventanas.  Puede tratar de crear un archivo preprocesado \([\/P](../../build/reference/p-preprocess-to-a-file.md)\) y buscar el símbolo en él.