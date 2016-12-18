---
title: "Crear una aplicaci&#243;n MFC basada en formularios | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcforms.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [MFC], basadas en formularios"
  - "aplicaciones basadas en formularios"
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear una aplicaci&#243;n MFC basada en formularios
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un formulario es un cuadro de diálogo con controles que permiten a un usuario tener acceso a datos y, posiblemente, modificarlos.  Es posible que quiera desarrollar una aplicación en la que el usuario elija entre un conjunto de formularios.  Normalmente, una aplicación basada en formularios permite al usuario tener acceso a los formularios haciendo clic en **Nuevo** en el menú **Archivo**.  Una aplicación basada en cuadros de diálogo, que no ofrece a los usuarios tener acceso a una opción **Nuevo** en el menú **Archivo**, también se considera una aplicación basada en formularios.  
  
 Una aplicación basada en formularios de interfaz de un único documento \(SDI\) sólo permite que se ejecute una instancia de un formulario concreto cada vez.  Es posible ejecutar simultáneamente formularios distintos desde una aplicación basada en formularios SDI si se selecciona un formulario nuevo de la opción **Nuevo** en el menú **Archivo**.  
  
 Si crea una aplicación basada en formularios de interfaz de múltiples documentos \(MDI\), la aplicación permitirá el uso de varias instancias del mismo formulario.  
  
 Si crea una aplicación que admita varios documentos de nivel superior, el escritorio será la ventana primaria implícita del documento y el marco del documento no se restringirá al área de cliente de la aplicación.  Puede abrir varias instancias del documento, cada una con su marco, su menú y su icono de la barra de tareas.  Puede cerrar individualmente las instancias siguientes de los documentos, pero si selecciona la opción `Exit` en el menú **Archivo** de la instancia inicial, la aplicación cerrará todas las instancias.  
  
 Las aplicaciones SDI, MDI y de múltiples documentos de nivel superior son todas aplicaciones basadas en formularios y utilizan la arquitectura documento\/vista.  
  
 Cualquier aplicación basada en un cuadro de diálogo es, por definición, una aplicación basada en formularios.  Una aplicación basada en un cuadro de diálogo no utiliza la arquitectura documento\/vista, por lo que el programador deberá administrar los métodos de creación y acceso para sus propios formularios adicionales.  
  
 La clase base para aplicaciones basadas en formularios es [CFormView](../../mfc/reference/cformview-class.md).  Si la aplicación ofrece compatibilidad con bases de datos, también puede seleccionar cualquier clase que se derive de `CFormView`.  Un formulario es cualquier ventana derivada de `CFormView` o de cualquier clase que herede de `CFormView`.  
  
 Aunque use una clase base como [CView](../../mfc/reference/cview-class.md), podrá convertir posteriormente sus aplicaciones en aplicaciones basadas en formularios [agregando una clase MFC](../../mfc/reference/adding-an-mfc-class.md) derivada de `CFormView` y activando la casilla **Generar recursos DocTemplate** en el [Asistente para clases MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).  
  
 Cuando finalice el asistente, se abrirá el proyecto y, si seleccionó `CFormView` \(o una clase que herede de `CFormView`\) como clase base o creó una aplicación basada en un cuadro de diálogo, Visual C\+\+ abrirá el editor de cuadros de diálogo.  En este momento ya está preparado para diseñar su primer formulario.  
  
### Para empezar a crear un ejecutable MFC basado en formularios  
  
1.  Siga las instrucciones descritas en [Crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En la página [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC, active la casilla **Compatibilidad con la arquitectura documento\/vista**.  
  
3.  Seleccione **Documento único**, **Múltiples documentos** o **Múltiples documentos de nivel superior**.  
  
    > [!NOTE]
    >  Si elige una aplicación de interfaz SDI, MDI o de múltiples documentos de nivel superior, se establece `CView` de manera predeterminada como clase base de la vista de la aplicación en la página [Clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) del asistente.  Para crear una aplicación basada en formularios, debe seleccionar `CFormView` como clase base de la vista de la aplicación.  Tenga en cuenta que el asistente no proporciona compatibilidad con la impresión para una aplicación basada en formularios.  
  
4.  Establezca las demás opciones de proyecto que desee en las otras páginas del asistente.  
  
5.  Haga clic en **Finalizar** para generar la aplicación esqueleto.  
  
 Para obtener más información, vea:  
  
-   [Clases de vista derivadas](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternativas a la arquitectura documento\/vista](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Opciones de diseño de aplicaciones](../../mfc/application-design-choices.md)  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Vistas de formulario](../../mfc/form-views-mfc.md)   
 [Crear una aplicación MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Crear una aplicación MFC estilo Explorador Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)