---
title: "Administrar datos con variables de datos del documento | Microsoft Docs"
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
  - "clases [C++], Friend"
  - "clases de colección [C++], utilizado por objetos de documento"
  - "datos [MFC]"
  - "datos [MFC], documentos"
  - "datos del documento [C++]"
  - "documentos [C++], almacenamiento de datos"
  - "clases de confianza"
  - "variables miembro [C++], clase de documento"
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administrar datos con variables de datos del documento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implemente los datos del documento como las variables miembro de la clase del documento.  Por ejemplo, el programa scribble declarar un miembro de datos de `CObList` tipo \(una lista vinculada que almacena punteros a objetos de `CObject` .  Esta lista se utiliza para almacenar matrices de puntos que constituyen un gráfico de línea de diseño libre.  
  
 Cómo se implementa los datos miembro de documentos depende de la naturaleza de la aplicación.  Para ayudarle out, MFC proporciona el grupo de “clases de colección” — matrices, listas, y mapas \(diccionarios\), incluidas las colecciones basadas en las plantillas de C\+\+ \(junto con las clases que encapsulan una variedad de tipos de datos comunes como `CString`, `CRect`, `CPoint`, `CSize`, y `CTime`.  Para obtener más información sobre estas clases, vea [Información general de la biblioteca de clases](../mfc/class-library-overview.md) en *la referencia de MFC*.  
  
 Al definir los datos del miembro del documento, agregará normalmente funciones miembro a la clase document para establecer y obtener elementos de datos y realizar otras operaciones útiles en ellas.  
  
 Las vistas tienen acceso al objeto document mediante el puntero de la vista al documento, instalado en la vista en la hora de creación.  Puede recuperar este puntero en funciones miembro de una vista llamando a la función **GetDocument**miembro de `CView` .  Asegúrese de convertir este puntero a dispone del tipo de documento.  Se puede tener acceso a los miembros del documento público a través del puntero.  
  
 Si la transferencia de datos normalmente requiere acceso directo, o que deseo usar miembros privados de la clase del documento, puede desear crear una clase de vista una función friend \(en términos de C\+\+\) de la clase del documento.  
  
## Vea también  
 [Usar documentos](../mfc/using-documents.md)