---
title: "MFC COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC COM (MFC)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tecnología activa [C++]"
  - "controles ActiveX [C++], modelo de objetos COM"
  - "COM [C++], compatibilidad con MFC"
  - "MFC [C++], compatibilidad con COM"
  - "controles ActiveX en MFC [C++], compatibilidad COM en MFC"
  - "MFC COM [C++]"
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un subconjunto de MFC está diseñado para admitir COM, mientras que la mayoría de Active Template Library \(ATL\) está diseñado para la programación COM.  Esta sección de temas describe la compatibilidad de MFC con COM.  
  
 Las tecnologías activo \(como controles ActiveX, contención de documento activo, OLE, etc.\) utilizan el modelo de objetos componentes \(COM\) para permitir que los componentes de software para interactuar entre sí en un entorno conectado, independientemente del lenguaje con el que se crearon.  Las tecnologías activo se pueden utilizar para crear aplicaciones que se ejecutan en el escritorio o internet.  Para obtener más información vea [Introducción a COM](../atl/introduction-to-com.md) o [El modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363).  
  
 Las tecnologías activo incluyen tecnologías de cliente y servidor, incluidos los siguientes:  
  
-   [Contención de documento activo](../mfc/active-document-containment.md), se admite en las versiones 4.2 de MFC y versiones posteriores, permite a los usuarios ver [documentos activos](../mfc/active-documents.md) \(como Microsoft Excel o archivos de Word\) y que provoquen la interfaz completa de la aplicación nativa del documento en el área cliente completa de [contenedor de documentos activos](../mfc/active-document-containers.md) como el cuaderno o Microsoft Internet Explorer de Microsoft Office.  Los contenedores actuar como clientes, mientras que los documentos proporcionan [servidores de documentos activos](../mfc/active-document-servers.md).  Para obtener más información sobre cómo utilizar documentos activos en aplicaciones de internet, vea: [Documentos activos en internet](../mfc/active-documents-on-the-internet.md).  
  
-   Los controles ActiveX son objetos interactivos que se pueden utilizar en contenedores como un sitio Web.  Para obtener más información sobre los controles ActiveX, vea:  
  
    -   [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)  
  
    -   [Controles ActiveX en internet](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Información general: Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Actualizar un control ActiveX existente que se utilizará en internet](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Depurar un control ActiveX](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)  
  
-   El script activo controla el comportamiento integrado de uno o más controles ActiveX de un explorador o un servidor.  Para obtener más información sobre script activo, vea [Tecnología activa en internet](../mfc/active-technology-on-the-internet.md).  
  
-   [Automatización](../mfc/automation.md) \(antes conocido como automatización OLE\) permite a una aplicación manipular los objetos implementados en otra aplicación, o “exponer” objetos para que los puede tratarse.  
  
     El objeto automatizado puede ser local o [remote](../mfc/remote-automation.md) \(en otro equipo accesible a través de una red\).  Automatización está disponible para OLE y objetos COM.  
  
-   Esta sección también proporciona información sobre cómo escribir componentes COM con MFC, por ejemplo, en [Puntos de conexión](../mfc/connection-points.md).  
  
 Para obtener una explicación de lo que todavía se denomina OLE con lo que se denomina ahora tecnología activa, vea los temas de [OLE](../mfc/ole-in-mfc.md).  
  
 También, vea el artículo Q248019 de Knowledge Base: HOWTO: Evite el cuadro de diálogo No está disponible Desde Durante que aparece en el Servidor una operación de Lengthy COM.  
  
## En esta sección  
 [Contención de documento activo](../mfc/active-document-containment.md)  
  
 [Automatización](../mfc/automation.md)  
  
 [Automatización remota](../mfc/remote-automation.md)  
  
 [Puntos de conexión](../mfc/connection-points.md)  
  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)