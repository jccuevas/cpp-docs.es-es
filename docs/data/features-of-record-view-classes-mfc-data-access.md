---
title: "Caracter&#237;sticas de las clases de vistas de registros (acceso a datos MFC) | Microsoft Docs"
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
  - "clases de vista de registros"
  - "vistas de registros, clases"
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Caracter&#237;sticas de las clases de vistas de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede llevar a cabo una programación de acceso a datos basada en formularios con la clase [CFormView](../mfc/reference/cformview-class.md), pero [CRecordView](../mfc/reference/crecordview-class.md) y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) suelen ser clases más adecuadas para derivar.  Además de las características `CFormView`, `CRecordView` y `CDaoRecordView`:  
  
-   Proporcionan intercambio de datos de cuadro de diálogo \(DDX\) entre los controles del formulario y el objeto de conjunto de registros asociado.  
  
-   Controlan los comandos Mover primero, Mover siguiente, Mover anterior y Mover último para navegar por los registros del objeto de conjunto de registros asociado.  
  
-   Actualizan los cambios del registro actual cuando el usuario se desplace a otro registro.  
  
 Para obtener más información sobre la navegación, consulte [Vistas de registros: permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## Vea también  
 [Vistas de registros \(acceso a datos MFC\)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)