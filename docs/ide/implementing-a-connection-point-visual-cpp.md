---
title: "Implementar un punto de conexi&#243;n (Visual C++) | Microsoft Docs"
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
  - "puntos de conexión [C++], implementar"
  - "Asistente para implementar puntos de conexión [C++]"
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementar un punto de conexi&#243;n (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para implementar un punto de conexión mediante el Asistente para implementar puntos de conexión, debe contar con un proyecto creado como una aplicación COM ATL o bien como una aplicación MFC que sea compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
> [!NOTE]
>  Para obtener información acerca de cómo implementar puntos de conexión para un proyecto MFC, vea [Puntos de conexión](../mfc/connection-points.md).  
  
 Una vez creado el proyecto, para implementar un punto de conexión primero debe agregar un objeto ATL.  Para obtener una lista de los asistentes que agregan objetos a los proyectos ATL, vea [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).  
  
> [!NOTE]
>  El asistente no admite cuadros de diálogo ATL, servicios Web XML creados con servidor ATL, objetos de rendimiento ni contadores de rendimiento.  
  
 Un objeto conectable \(es decir, un origen\) puede exponer un punto de conexión por cada una de sus interfaces de salida.  Cada interfaz de salida puede ser implementada por un cliente sobre un objeto \(es decir, un receptor\).  Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).  
  
### Para implementar un punto de conexión  
  
1.  En la Vista de clases, haga clic con el botón secundario en el nombre de la clase del objeto ATL.  
  
2.  Haga clic en **Agregar** del menú contextual y, a continuación, haga clic en **Agregar punto de conexión**. Se ejecuta el [Asistente para implementar puntos de conexión](../ide/implement-connection-point-wizard.md).  
  
3.  Seleccione las interfaces de punto de conexión que desee implementar en las bibliotecas de tipos apropiadas y haga clic en **Finalizar**.  
  
4.  En la Vista de clases, examine las clases de proxy creadas para cada punto de conexión.  Las clases aparecen como CProxy*NombreDeInterfaz*\<T\> y se derivan de [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Haga doble clic en la clase del punto de conexión para mostrar la definición de la clase.  
  
    -   Si implementa un punto de conexión para la interfaz de su propio proyecto, aparece la siguiente descripción:  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Si implementa una interfaz local, aparecen los métodos y propiedades en el cuerpo de la clase.  
  
    -   Si implementa un punto de conexión para otra interfaz, la definición incluye los métodos de la interfaz, precedidos de `Fire_`.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Adding Connection Points to an Object](../atl/adding-connection-points-to-an-object.md)