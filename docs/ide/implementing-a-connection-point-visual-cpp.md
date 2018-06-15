---
title: Implementar un punto de conexión (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b75bf145da401ad9889353a1e65448831c602c9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328352"
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementar un punto de conexión (Visual C++)
Para implementar un punto de conexión mediante el Asistente para implementar puntos de conexión, debe haber creado un proyecto como una aplicación COM de ATL o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
> [!NOTE]
>  Para obtener información sobre cómo implementar puntos de conexión para un proyecto MFC, vea [Puntos de conexión](../mfc/connection-points.md).  
  
 Una vez creado el proyecto, para implementar un punto de conexión, primero debe agregar un objeto ATL. Vea [Agregar controles y objetos a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos a los proyectos ATL.  
  
> [!NOTE]
>  El asistente no admite cuadros de diálogo de ATL, servicios web XML creados con Servidor ATL, objetos de rendimiento ni contadores de rendimiento.  
  
 Un objeto conectable (es decir, un origen) puede exponer un punto de conexión para cada una de sus interfaces de salida. Cada interfaz de salida se puede implementar mediante un cliente en un objeto (es decir, un receptor). Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).  
  
### <a name="to-implement-a-connection-point"></a>Para implementar un punto de conexión  
  
1.  En la Vista de clases, haga clic con el botón derecho en el nombre de clase para el objeto ATL.  
  
2.  Haga clic en **Agregar** desde el menú contextual y después en **Agregar punto de conexión** para mostrar el [Asistente para implementar puntos de conexión](../ide/implement-connection-point-wizard.md).  
  
3.  Seleccione las interfaces de punto de conexión que se van a implementar desde las bibliotecas de tipos adecuadas y haga clic en **Finalizar**.  
  
4.  En la Vista de clases, examine las clases de proxy creadas para cada punto de conexión. Las clases aparecen como CProxy*NombreDeInterfaz*\<T> y se derivan de [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Haga doble clic en la clase de punto de conexión para mostrar la definición de clase del punto de conexión.  
  
    -   Si implementa un punto de conexión para la interfaz de un proyecto propio, aparecerá la definición siguiente:  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Si implementa una interfaz local, en el cuerpo de la clase aparecerán métodos y propiedades.  
  
    -   Si implementa un punto de conexión para otra interfaz, la definición incluye los métodos de la interfaz, precedidos de `Fire_`.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar puntos de conexión a un objeto](../atl/adding-connection-points-to-an-object.md)