---
title: "Recommendations for Choosing Between ATL and MFC | Microsoft Docs"
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
  - "ATL, MFC"
  - "MFC, ATL support"
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Recommendations for Choosing Between ATL and MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al desarrollar componentes y aplicaciones, puede elegir entre dos enfoques — ATL y MFC \(la biblioteca Microsoft Foundation Class\).  
  
## Utilizar ATL  
 ATL es un rápido, la manera fácil a crea un componente COM en C\+\+ y mantiene una pequeña superficie.  Utilice ATL para crear un control si no se necesita toda la funcionalidad integrada que MFC automáticamente proporciona.  
  
## Utilizar MFC  
 MFC permite crear aplicaciones completas, los controles ActiveX, y los documentos activos.  Si ya ha creado un control con MFC, puede desear continuar el desarrollo en MFC.  Al crear un nuevo control, considere utilizar ATL si no se necesita toda la funcionalidad integrada de MFC.  
  
## Mediante ATL en un proyecto MFC  
 Puede agregar compatibilidad para utilizar ATL en un proyecto MFC existente ejecutando un asistente.  Para obtener información detallada, vea [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## Vea también  
 [Introducción a ATL](../atl/introduction-to-atl.md)