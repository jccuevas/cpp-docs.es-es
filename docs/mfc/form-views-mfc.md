---
title: "Vistas de formulario (MFC) | Microsoft Docs"
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
  - "aplicaciones [MFC], basadas en formularios"
  - "formularios [C++]"
  - "formularios [C++], agregar a aplicaciones"
  - "aplicaciones basadas en formularios"
  - "interfaces de usuario, formularios"
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Vistas de formulario (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede agregar los formularios a cualquier aplicación de Visual C\+\+ que admite las bibliotecas MFC, incluidos [aplicación formulario\-basada](../mfc/reference/creating-a-forms-based-mfc-application.md) \(una cuya clase de vista se deriva de `CFormView`\).  Si no creó inicialmente la aplicación para admitir los formularios, Visual C\+\+ agregará esta compatibilidad automáticamente cuando se inserta un nuevo formulario.  En una aplicación SDI o MDI, que implementa [arquitectura documento\/vista](../mfc/document-view-architecture.md)predeterminado, cuando el usuario elige el comando de `New` \(de forma predeterminada, en el menú de **archivo** \), Visual C\+\+ pide al usuario elegir entre formularios disponibles.  
  
 Con una aplicación SDI, cuando el usuario elige el comando de `New` , la instancia actual del formulario continúa ejecutándose pero una nueva instancia de la aplicación con el formulario seleccionado se crea si no se encuentra.  En una aplicación MDI, la instancia actual del formulario continúa ejecutándose cuando el usuario elige el comando de `New` .  
  
> [!NOTE]
>  Puede insertar un formulario en una aplicación diálogo\- basada \(una cuyo tipo de cuadro de diálogo se basa en `CDialog` y una en la que no se implementa ninguna clase de vista\).  Sin embargo, sin la arquitectura documento\/vista, Visual C\+\+ automáticamente no implementa **archivo** &#124;funcionalidad de**new** .  Debe crear una manera para que el usuario vea formularios adicionales, como implementar un cuadro de diálogo con fichas que muestra las distintas páginas de propiedades.  
  
 Cuando se inserta un nuevo formulario en la aplicación, Visual C\+\+ hace lo siguiente:  
  
-   Crea una clase basada en una de las clases de formulario\- estilo que elija \(`CFormView`, `CRecordView`, `CDaoRecordView`, o `CDialog`\).  
  
-   Crea un recurso de cuadro de diálogo con estilos adecuados \(o puede utilizar un recurso existente del diálogo que aún no se ha asociado a una clase\).  
  
     Si elige un recurso existente del cuadro de diálogo, puede ser necesario establecer estos estilos mediante la página de propiedades del cuadro de diálogo.  Los estilos para un cuadro de diálogo deben incluir:  
  
     \=On De**WS\_CHILD**  
  
     \=Off de`WS_BORDER`  
  
     \=Off De**WS\_VISIBLE**  
  
     **WS\_CAPTION\=**desactivado  
  
 Para las aplicaciones basadas en la arquitectura documento\/vista, el comando de **New Form** \(haga clic con el botón secundario en la vista de clases\) también:  
  
-   Crea **CDocument**\- clase basada  
  
     En lugar de hacer una nueva clase crear, puede utilizar cualquier **CDocument**existente \(clase basada en el proyecto.  
  
-   Representa una plantilla de documento \(derivada de **CDocument**\) con la cadena, menú, y los recursos de icono.  
  
     También puede crear una nueva clase en la que se basará la plantilla.  
  
-   Agregue una llamada a **AddDocumentTemplate** en el código de `InitInstance` de la aplicación.  
  
     Visual C\+\+ agrega este código para cada nuevo formulario que crea, que agrega el formulario a la lista de formularios disponible cuando el usuario elige el comando de `New` .  Este código incluye el Id. de recurso asociado y los nombres del documento, de la vista, y de las clases asociados de marco que juntos constituyen el nuevo objeto de formulario.  
  
     Las plantillas de documento sirven como conexión entre documentos, las ventanas de marco, y las vistas.  Para un único documento, puede crear muchas plantillas.  
  
 Para obtener más información, vea:  
  
-   [Cree una aplicación Formulario\-basada](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Insertar un formulario en un proyecto](../mfc/inserting-a-form-into-a-project.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)