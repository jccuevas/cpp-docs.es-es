---
title: "Compatibilidad de ATL con controles DHTML | Microsoft Docs"
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
  - "controles DHTML"
  - "controles DHTML, compatibilidad con ATL"
  - "controles HTML, compatibilidad con ATL"
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Compatibilidad de ATL con controles DHTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mediante ATL, puede crear un control con capacidad de HTML dinámico \(DHTML\).  Un control ATL DHTML:  
  
-   Hospeda el control WebBrowser.  
  
-   Especifica, mediante HTML, la interfaz de usuario \(UI\) de control DHTML.  
  
-   Tiene acceso al objeto WebBrowser y sus métodos a través de su interfaz, [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx).  
  
-   Administra la comunicación entre el código de C\+\+ y HTML.  
  
 Un control DHTML es similar a cualquier otro control ATL, a menos que el control DHTML incluye una interfaz de envío adicional.  Vea la ilustración de [Identificar los elementos de proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) para una ilustración de interfaces proporcionadas en el proyecto DHTML predeterminado.  
  
 Puede ver el control ATL DHTML en el explorador web u otro contenedor, como el ActiveX control test container.  
  
## En esta sección  
 [Identificar los elementos de proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)  
 Describe los elementos de un proyecto de control DHTML.  
  
 [Llamada C\+\+ codificadas de DHTML](../atl/calling-cpp-code-from-dhtml.md)  
 Proporciona un ejemplo de llamar al código de C\+\+ de un control DHTML.  
  
 [Crear un Control ATL DHTML](../atl/creating-an-atl-dhtml-control.md)  
 Muestra los pasos para crear un control DHTML.  
  
 [Probar el Control ATL DHTML](../atl/testing-the-atl-dhtml-control.md)  
 Muestra cómo compilar y probar el proyecto de control inicial de DHTML.  
  
 [Modificación de Control ATL DHTML](../atl/modifying-the-atl-dhtml-control.md)  
 Muestra cómo agregar alguna funcionalidad al control.  
  
 [Probar el Control modificada ATL DHTML](../atl/testing-the-modified-atl-dhtml-control.md)  
 Muestra cómo compilar y probar la funcionalidad agregada del control.  
  
## Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas conceptuales sobre cómo programar utilizando Active Template Library.