---
title: "Trabajar con documentos y vistas | Microsoft Docs"
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
  - "documentos [C++], MFC"
  - "MFC [C++], documentos"
  - "MFC [C++], vistas"
  - "vistas [C++], MFC"
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trabajar con documentos y vistas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca Microsoft Foundation Classes \(MFC\) se basa en una arquitectura documento\/vista para muchas de sus características.  Normalmente, un documento almacena los datos y una vista los muestra dentro del área de cliente de una ventana de marco y administra la interacción del usuario con los datos.  La vista se comunica con el documento para obtener y actualizar los datos.  Las clases de base de datos se pueden usar con el marco de trabajo o sin él.  
  
 Para obtener más información sobre cómo se utilizan clases de base de datos en el marco de trabajo, vea [MFC: Utilizar clases de base de datos con documentos y vistas](../../data/mfc-using-database-classes-with-documents-and-views.md).  
  
 De manera predeterminada, el Asistente para aplicaciones MFC crea una "aplicación esqueleto" que no es compatible con bases de datos.  Sin embargo, se pueden seleccionar opciones para incluir una compatibilidad mínima con bases de datos o una compatibilidad más completa basada en formularios.  Para obtener más información sobre las opciones del asistente para aplicaciones, vea [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md).  
  
 También se pueden utilizar clases de base de datos sin usar la arquitectura documento\/vista completa.  Para obtener más información, vea [MFC: Utilizar clases de base de datos sin documentos ni vistas](../../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)