---
title: "Implementar un punto de conexión (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab065c78d8ea5d2de105abdc2fa651e05f9d1875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementar un punto de conexión (Visual C++)
Para implementar un punto de conexión mediante el Asistente de punto de conexión de implementar, debe haber creado un proyecto como una aplicación ATL COM o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
> [!NOTE]
>  Para obtener información acerca de cómo implementar puntos de conexión para un proyecto MFC, vea [puntos de conexión](../mfc/connection-points.md).  
  
 Una vez creado el proyecto, para implementar un punto de conexión, primero debe agregar un objeto ATL. Vea [agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos a los proyectos ATL.  
  
> [!NOTE]
>  El asistente no admite cuadros de diálogo ATL, servicios Web XML creados con servidor ATL, objetos de rendimiento ni contadores de rendimiento.  
  
 Un objeto conectable (es decir, un origen) puede exponer un punto de conexión para cada una de sus interfaces de salida. Cada interfaz de salida puede ser implementada por un cliente en un objeto (es decir, un receptor). Para obtener más información, consulte [puntos de conexión ATL](../atl/atl-connection-points.md).  
  
### <a name="to-implement-a-connection-point"></a>Para implementar un punto de conexión  
  
1.  En la vista de clases, haga clic en el nombre de clase para el objeto ATL.  
  
2.  Haga clic en **agregar** desde el menú contextual y, a continuación, haga clic en **agregar punto de conexión** para mostrar la [Asistente para implementar puntos de conexión](../ide/implement-connection-point-wizard.md).  
  
3.  Seleccione las interfaces de punto de conexión para implementar en las bibliotecas de tipo adecuado y haga clic en **finalizar**.  
  
4.  En la vista de clases, examine las clases de proxy creadas para cada punto de conexión. Las clases aparecen como CProxy*InterfaceName*\<T > y se derivan [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Haga doble clic en la clase de punto de conexión para mostrar la definición de clase del punto de conexión.  
  
    -   Si implementa un punto de conexión para la interfaz de su propio proyecto, aparece la siguiente definición  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Si implementa una interfaz local, métodos y propiedades aparecen en el cuerpo de la clase.  
  
    -   Si implementa un punto de conexión para otra interfaz, la definición incluye los métodos de la interfaz, precedidos de `Fire_`.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar puntos de conexión a un objeto](../atl/adding-connection-points-to-an-object.md)