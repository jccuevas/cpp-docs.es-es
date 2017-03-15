---
title: "Derivar una clase de documento de CDocument | Microsoft Docs"
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
  - "CDocument (clase), derivar de"
  - "clases [C++], derivar de CDocument"
  - "clases derivadas, funciones que se reemplazan con frecuencia"
  - "clases de documento, funciones que se reemplazan con frecuencia"
  - "objetos de documentos, derivadas"
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Derivar una clase de documento de CDocument
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los documentos contienen y administran los datos de aplicación.  Para usar la aplicación MFC Asistente\- proporcionó la clase document, debe hacer lo siguiente:  
  
-   Derive una clase de **CDocument** para cada tipo de documento.  
  
-   Agregue las variables miembro para almacenar los datos de cada documento.  
  
-   Función miembro de **CDocument**`Serialize` de reemplazo de la clase del documento.  `Serialize` escribe y lee los datos del documento a y desde el disco.  
  
## Otras funciones de documento invalidan a menudo  
 Puede que también desee reemplazar otras funciones miembro de **CDocument** .  En particular, a menudo necesitará invalidar [OnNewDocument](../Topic/CDocument::OnNewDocument.md) y [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) para inicializar los miembros de datos y [DeleteContents](../Topic/CDocument::DeleteContents.md) de documento destruir datos dinámicamente asignados.  Para obtener información sobre los miembros reemplazables, vea la clase [CDocument](../mfc/reference/cdocument-class.md) en *la referencia de MFC*.  
  
## Vea también  
 [Usar documentos](../mfc/using-documents.md)