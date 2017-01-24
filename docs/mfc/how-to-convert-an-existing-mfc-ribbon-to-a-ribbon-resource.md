---
title: "C&#243;mo: Convertir una cinta de MFC existente en un recurso de cinta | Microsoft Docs"
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
  - "cinta MFC, convertir a un recurso de cinta"
  - "recurso de cinta, convertir de una cinta MFC"
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir una cinta de MFC existente en un recurso de cinta
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los recursos de la cinta de opciones son más fáciles de visualizar, de modificar, y mantener que las cintas de opciones manualmente codificadas.  En este tema se describe cómo convertir una cinta manualmente codificada en un proyecto MFC en un recurso de la cinta de opciones.  
  
 Debe tener un proyecto MFC existente que tenga código que usa clases de la cinta de MFC, por ejemplo, [Clase de CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md).  
  
### Para convertir una cinta de MFC a un recurso de la cinta de opciones  
  
1.  En Visual Studio, en un proyecto MFC existente, abra el archivo de código fuente donde se inicializa el objeto de CMFCRibbonBar.  Normalmente, el archivo es mainfrm.cpp.  Agregue el código siguiente después del código de inicialización de la cinta de opciones.  
  
    ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");  
    ```  
  
     Guarde y cierre el archivo.  
  
2.  Compile y ejecute la aplicación MFC y, en el Bloc de notas, abra RibbonOutput.txt y copie su contenido.  
  
3.  En Visual Studio, en el menú de **Project** , haga clic en **Agregar recurso**.  En el cuadro de diálogo **Agregar recurso**, seleccione **Cinta** y, a continuación, haga clic en **Nueva**.  
  
     Visual Studio crea un recurso de la cinta de opciones y lo abre en la vista diseño.  El identificador de recurso de cinta es IDR\_RIBBON1, que se muestra en la **Vista de recursos**.  La cinta de opciones se define en el archivo XML de ribbon1.mfcribbon\-ms.  
  
4.  En Visual Studio, ribbon1.mfcribbon\-ms abierto, elimine su contenido y, a continuación pegue el contenido de RibbonOutput.txt, que copió anteriormente.  Guarde y cierre ribbon1.mfcribbon\-ms.  
  
5.  Abra de nuevo el archivo de código fuente donde se inicializa el objeto de CMFCRibbonBar \(normalmente, mainfrm.cpp\) y marque como comentario el código existente de la cinta de opciones.  Agregue el código siguiente después del código que se marcados como comentario.  
  
    ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
6.  Compile el proyecto y ejecute el programa.  
  
## Vea también  
 [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md)