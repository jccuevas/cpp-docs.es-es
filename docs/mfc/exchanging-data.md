---
title: "Intercambiar datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDX (intercambio de datos de cuadros de diálogo), hojas de propiedades"
  - "intercambiar datos con hojas de propiedades"
  - "hojas de propiedades, intercambio de datos"
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Intercambiar datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como la mayoría de los cuadros de diálogo, el intercambio de datos entre la hoja de propiedades y la aplicación es una de las funciones más importantes de la hoja de propiedades.  En este artículo se describe cómo realizar esta tarea.  
  
 Intercambiar datos con una hoja de propiedades es realmente una cuestión de intercambiar datos con páginas de propiedades individuales de la hoja de propiedades.  El procedimiento para intercambiar datos con una página de propiedades es igual que para intercambiar datos con un cuadro de diálogo, ya que un objeto de [CPropertyPage](../mfc/reference/cpropertypage-class.md) es simplemente un objeto especializado de [CDialog](../mfc/reference/cdialog-class.md) .  El procedimiento aprovecha la facilidad de intercambio de datos del cuadro de diálogo de marco \(DDX\), que intercambia datos entre los controles en un cuadro de diálogo y las variables miembro del objeto del cuadro de diálogo.  
  
 La diferencia importante entre intercambiar datos con una hoja de propiedades y con un cuadro de diálogo normal es que la hoja de propiedades tiene varias páginas, por lo que debe intercambiar datos con todas las páginas de la hoja de propiedades.  Para obtener más información sobre DDX, vea [Diálogo Data Exchange y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
 El ejemplo siguiente muestra intercambiando datos entre una vista y dos páginas de una hoja de propiedades:  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/CPP/exchanging-data_1.cpp)]  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)