---
title: "Identifying the Elements of the DHTML Control Project | Microsoft Docs"
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
  - "DHTML controls, ATL support"
  - "controles HTML, ATL support"
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Identifying the Elements of the DHTML Control Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código de control DHTML es exactamente igual que creó para cualquier control ATL.  Para una introducción básica de código genérico, el trabajo con [tutorial de ATL](../atl/active-template-library-atl-tutorial.md), y leer las secciones [Crear un proyecto ATL](../atl/reference/creating-an-atl-project.md) y [Fundamentos de objetos COM de ATL](../atl/fundamentals-of-atl-com-objects.md).  
  
 Un control DHTML es similar a cualquier control ATL, excepto:  
  
-   Además de las interfaces regulares un control implementa, implementa una interfaz adicional que se utiliza para la comunicación entre el código de C\+\+ y la interfaz de usuario \(UI\) HTML.  Las llamadas de interfaz de usuario HTML en el código de C\+\+ mediante esta interfaz.  
  
-   Crea un recurso de HTML para la interfaz de usuario del control.  
  
-   Permite el acceso al modelo de objetos de DHTML a través de la variable miembro `m_spBrowser`, que es un puntero inteligente de [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)escrito.  Utilice este puntero para tener acceso a cualquier parte del modelo de objetos de DHTML.  
  
 El gráfico siguiente muestra la relación entre el archivo DLL, el control DHTML, el explorador web, y el recurso de HTML.  
  
 ![Elementos de un proyecto de control DHTML](../atl/media/vc52en1.png "vc52EN1")  
  
> [!NOTE]
>  Los nombres de este gráfico son marcadores.  Los nombres de recurso de HTML y de las interfaces expuestas en el control se basan en los nombres que se asignan en el asistente para controles ATL.  
  
 en este gráfico, los elementos son:  
  
-   **My DLL** The DLL creado mediante el asistente para proyectos ATL.  
  
-   Control de**Control DHTML** \(`m_spBrowser`\) The DHTML, creado con el asistente para objetos ATL.  Este control tiene acceso al objeto del explorador web y sus métodos a través de la interfaz del objeto de explorador web, **IWebBrowser2**.  El propio control expone las dos interfaces siguientes, además de las otras interfaces estándar necesarias para un control.  
  
    -   Interfaz de**IDHCTL1** The expuesta por el control para utilizarlo sólo en el contenedor.  
  
    -   Interfaz de envío de**IDHCTLUI1** The para comunicarse entre el código de C\+\+ y la interfaz de usuario HTML.  El explorador web utiliza la interfaz de envío del control para mostrar el control.  Puede llamar a varios métodos de esta interfaz de envío de la interfaz de usuario del control invocando `window.external`, seguidos por el nombre del método de esta interfaz de envío que desea invocar.  Se obtiene acceso a `window.external` de una etiqueta de SCRIPT dentro de HTML que constituye la interfaz de usuario para este control.  Para obtener más información sobre cómo invocar métodos externos en el archivo de recursos, vea [Código de C\+\+ de llamada DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   Id. de recurso de**IDR\_CTL1** el recurso de HTML.  El nombre de archivo, en este caso, es ADO CTL1 UI.htm.  El control DHTML utiliza un recurso de HTML que contiene las etiquetas HTML estándar y comandos externos de envío de la ventana que puede modificar con el editor de texto.  
  
-   El explorador web de**Web Browser** The muestra la interfaz de usuario del control, basándose en HTML en el recurso de HTML.  Un puntero a la interfaz de **IWebBrowser2** de explorador web está disponible en el control DHTML permitir el acceso al modelo de objetos de DHTML.  
  
 El asistente para controles ATL genera un control con código predeterminado en el recurso de HTML y el archivo .cpp.  Puede compilar y ejecutar el control que se genera en el asistente, y después ver el control en el explorador web o el ActiveX control test container.  La imagen siguiente muestra el control predeterminado ATL DHTML con tres botones mostrados en contenedor de prueba:  
  
 ![Control DHTML ATL](../atl/media/vc52en2.png "vc52EN2")  
  
 Vea [Crear un Control ATL DHTML](../atl/creating-an-atl-dhtml-control.md) para empezar a crear un control DHTML.  Vea [Propiedades y eventos de pruebas con el contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso al contenedor de prueba.  
  
## Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)