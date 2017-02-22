---
title: "Cadenas, Asistente para p&#225;ginas de propiedades ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.ppg.strings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para páginas de propiedades ATL, cadenas"
ms.assetid: 00547db6-911f-49eb-92e1-2ba67079d4df
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Cadenas, Asistente para p&#225;ginas de propiedades ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona el texto asociado a la página de propiedades.  
  
 **Título**  
 Define el texto que aparece en la ficha de la página de propiedades.  
  
 **Cadena del documento**  
 Define una cadena de texto que describe la página.  La cadena puede mostrarse en el cuadro de diálogo de la hoja de propiedades.  El marco de propiedad puede usar la descripción en una línea de estado o en la información sobre herramientas.  El marco de propiedad estándar por el momento no usa esta cadena.  
  
 **Archivo de ayuda**  
 Define el nombre del archivo de ayuda donde se explica la utilización de la página de propiedades.  Dicho nombre no debe incluir una ruta de acceso.  Cuando el usuario elige **Ayuda**, el marco abre el archivo de ayuda en el directorio contenido en el valor de la clave HelpDir, en las entradas del Registro de la página de propiedades bajo su CLSID.  
  
## Vea también  
 [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)   
 [Opciones, Asistente para páginas de propiedades ATL](../../atl/reference/options-atl-property-page-wizard.md)