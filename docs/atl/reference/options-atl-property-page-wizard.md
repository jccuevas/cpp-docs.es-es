---
title: "Opciones, Asistente para p&#225;ginas de propiedades ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.ppg.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para páginas de propiedades ATL, opciones"
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Opciones, Asistente para p&#225;ginas de propiedades ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use esta página del asistente para definir el modelo de subprocesos y el nivel de agregación de la página de propiedades que está creando.  
  
 **Modelo de subprocesos**  
 Especifica el modelo de subprocesos que usa la página de propiedades.  
  
 Para obtener más información, vea [Especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md).  
  
|Opción|Descripción|  
|------------|-----------------|  
|`Single`|La página de propiedades sólo se ejecuta en el subproceso principal de COM .|  
|**Apartamento**|La página de propiedades puede crearse en cualquier apartamento de un único subproceso.  Es el formato predeterminado.|  
  
 **Agregación**  
 Proporciona compatibilidad con la agregación en la página de propiedades que se está creando.  Vea [Agregación](../../atl/aggregation.md) para obtener más información.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Sí**|Crea una página de propiedades que puede agregarse.|  
|**No**|Crea una página de propiedades que no puede agregarse.|  
|**Sólo**|Crea una página de propiedades cuyas instancias sólo pueden crearse mediante agregación.|  
  
## Vea también  
 [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)   
 [Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)