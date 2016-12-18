---
title: "MAPI | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "correo electrónico, habilitar"
  - "habilitar aplicaciones de correo"
  - "habilitar aplicaciones de MAPI"
  - "correo, habilitar la aplicación"
  - "compatibilidad MAPI en MFC"
  - "MAPI, MFC"
  - "mensajería, aplicaciones cliente"
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MAPI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe la Interfaz de programación de aplicaciones de mensajería \(MAPI\) de Microsoft para los programadores de aplicaciones de mensaje de cliente.  La compatibilidad de MFC con un subconjunto de MAPI en la clase **CDocument** pero no encapsula API completo.  Para obtener más información, vea [Compatibilidad con MAPI en MFC](../mfc/mapi-support-in-mfc.md).  
  
 MAPI es un conjunto de funciones que las aplicaciones habilitadas para correo y correo\- con conocimiento pleno utilizan para crear, manipular, para transferir, y almacenar mensajes de correo.  Proporciona a los programadores de aplicaciones herramientas para definir el propósito y el contenido de los mensajes de correo y les proporciona flexibilidad en la administración de mensajes de correo almacenados.  MAPI también proporciona una interfaz común que los desarrolladores de aplicaciones pueden usar para crear como independientes habilitada para correo y correo\- reconozca de aplicaciones de sistema de mensajería subyacente.  
  
 Los clientes de mensajería proporcionan una interfaz humana para la interacción con el sistema de mensajería de Microsoft Windows \(WMS\).  Esta interacción incluye normalmente solicitar servicios de los proveedores de MAPI\- bajo como mensaje almacena y las libros de direcciones.  
  
 Para obtener más información sobre MAPI, vea los artículos en la guía en la API de Win32 \(MAPI\) de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## En esta sección  
 [Compatibilidad con MAPI en MFC](../mfc/mapi-support-in-mfc.md)  
  
## Vea también  
 [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)   
 [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)   
 [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)