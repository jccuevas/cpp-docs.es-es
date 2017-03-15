---
title: "Servidores de documentos activos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "servidores de documentos activos [C++]"
  - "documentos activos [C++], servidores"
  - "servidores [C++], documento activo"
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Servidores de documentos activos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los servidores del documento activo como documentos de host de word, de Excel, o de PowerPoint de otros tipos de aplicación denominado documentos activos.  A diferencia de los objetos incrustados OLE \(que se muestran simplemente dentro de la página de otro documento\), los documentos activos proporcionan la interfaz completa y completan la funcionalidad nativa de la aplicación de servidor que se crean.  Los usuarios pueden crear documentos utilizando los plenos poderes de sus aplicaciones favoritas \(si son documento activo habilitada, todavía pueden tratar el proyecto resultante como una entidad única.  
  
 Los documentos activos pueden tener más de una página y siempre están activas en contexto.  Elemento control de documentos activos de la interfaz de usuario, combinando los menús con menús de **archivo** y de **Ay&uda** del contenedor.  Ocupan el área de edición completa de contenedor y controlan las vistas y el diseño de páginas de la impresora \(márgenes, pies de página, etc.\).  
  
 MFC implementa en los servidores del documento activo con interfaces de documento y vista, los mapas del envío de un comando, impresión, la administración de menú, y la administración del registro.  Los requisitos concretos de programación se tratan en [documentos activos](../mfc/active-documents.md).  
  
 MFC admite documentos activos con la clase de [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) , derivada de [CCmdTarget](../mfc/reference/ccmdtarget-class.md), y de [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), derivado de [COleServerItem](../mfc/reference/coleserveritem-class.md).  MFC admite los contenedores del documento activo con la clase de [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) , derivada de [COleClientItem](../mfc/reference/coleclientitem-class.md).  
  
 `CDocObjectServer` asigna las interfaces del documento activo y inicializa y genera un documento activo.  MFC también ofrece macros al enrutamiento de comandos ID en documentos activos.  Para utilizar documentos activos en la aplicación, incluya AfxDocOb.h en el archivo StdAfx.h.  
  
 Un servidor MFC de archivo enlaza de su propio `COleServerItem`\- clase derivada.  El Asistente para aplicaciones MFC genera esta clase automáticamente si activa la casilla de **Mini\-server** o de **Full\-server** del servidor de aplicaciones compatibilidad de documento compuesto.  Si también active la casilla de **Active document server** , Asistente para aplicaciones MFC genera una clase derivada de `CDocObjectServerItem` en su lugar.  
  
 La clase de `COleDocObjectItem` permite que un contenedor OLE se convierta en un contenedor de documentos activos.  Puede utilizar el Asistente para aplicaciones MFC para crear un contenedor de documento activo activando la casilla de **Active document container** en la página de soporte de documento compuesto del Asistente para aplicaciones MFC.  Para obtener más información, vea [Crear una aplicación contenedora de documentos activos](../mfc/creating-an-active-document-container-application.md).  
  
## Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)