---
title: "Dise&#241;ador de la cinta de opciones (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.ribbon.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "diseñador de la cinta de opciones de MFC"
  - "diseñador de la cinta de opciones (MFC)"
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dise&#241;ador de la cinta de opciones (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El diseñador de la cinta de opciones permite crear y personalizar las cintas de opciones de las aplicaciones MFC.  Una cinta de opciones es un elemento de la interfaz de usuario \(IU\) que organiza los comandos en grupos lógicos.  Estos grupos aparecen en pestañas independientes en una banda a lo largo de la parte superior de la ventana.  La cinta de opciones reemplaza a la barra de menús y a las barras de herramientas.  Una cinta de opciones puede mejorar considerablemente la facilidad de uso de la aplicación.  Para obtener más información, vea [Cintas de opciones](https://msdn.microsoft.com/es-es/library/cc872782.aspx).  En la siguiente ilustración se muestra una cinta de opciones.  
  
 ![Control de recursos de la cinta de opciones de MFC](../mfc/media/ribbon_no_callouts.png "Ribbon\_No\_Callouts")  
  
 En versiones anteriores de Visual Studio, las cintas de opciones se tenían que crear escribiendo código que emplee las clases de la cinta de opciones MFC, como [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md).  En [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], el diseñador de la cinta de opciones proporciona un método alternativo para la creación de las cintas de opciones. En primer lugar, cree y personalice una cinta de opciones como un recurso.  A continuación, cargue el recurso de cinta de opciones desde el código en la aplicación MFC.  Incluso puede usar los recursos de cinta de opciones y las clases de cinta de opciones MFC juntos.  Por ejemplo, puede crear un recurso de cinta de opciones y, a continuación, agregarle mediante programación más elementos en tiempo de ejecución con el código.  
  
## Descripción del diseñador de la cinta de opciones  
 El diseñador de la cinta de opciones crea y almacena la cinta de opciones como un recurso.  Cuando se crea un recurso de cinta de opciones, el diseñador de la cinta de opciones hace estas tres cosas:  
  
-   Agrega una entrada en el script de definición de recursos de proyecto \(\*.rc\).  En el ejemplo siguiente, `IDR_RIBBON` es el nombre único que identifica el recurso de cinta de opciones, `RT_RIBBON_XML` es el tipo de recurso y `ribbon.mfcribbon-ms` es el nombre del archivo de recursos.  
  
    ```  
    IDR_RIBBON             RT_RIBBON_XML                      "res\\ribbon.mfcribbon-ms"  
    ```  
  
-   Agrega las definiciones de identificadores de comando a resource.h.  
  
    ```  
    #define IDR_RIBBON            307  
    ```  
  
-   Crea un archivo de recursos de cinta de opciones \(\*.mfcribbon\-ms\) que contiene el código XML que define los botones, los controles y los atributos de la cinta de opciones.  Los cambios realizados en la cinta de opciones en el diseñador de la cinta de opciones se almacenan en el archivo de recursos como XML.  En el ejemplo de código siguiente se muestra parte del contenido de un archivo \*.mfcribbon\-ms:  
  
    ```  
    <RIBBON_BAR>  
      <ELEMENT_NAME>RibbonBar</ELEMENT_NAME>  
      <IMAGE>  
        <ID>  
          <NAME>IDB_BUTTONS</NAME>  
          <VALUE>113</VALUE>  
        </ID> …  
    ```  
  
 Para usar el recurso de cinta de opciones en la aplicación MFC, cárguelo mediante una llamada a [CMFCRibbonBar::LoadFromResource](../Topic/CMFCRibbonBar::LoadFromResource.md).  
  
## Crear una cinta de opciones mediante el diseñador de la cinta de opciones  
 Estas son las dos maneras de agregar un recurso de cinta de opciones al proyecto MFC:  
  
-   Cree una aplicación MFC y configure el Asistente para proyectos MFC para crear la cinta de opciones.  Para obtener más información, vea [Tutorial: Crear una aplicación de cinta usando MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).  
  
-   En un proyecto MFC existente, cree un recurso de cinta de opciones y cárguelo.  Para obtener más información, vea [Tutorial: Actualizar la aplicación Scribble de MFC \(Parte 1\)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
 Si el proyecto ya tiene una cinta de opciones codificada de forma manual, MFC tiene funciones que puede utilizar para convertir la cinta existente en un recurso de cinta de opciones.  Para obtener más información, vea [Cómo: Convertir una cinta de MFC existente en un recurso de cinta](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).  
  
> [!NOTE]
>  Las cintas de opciones no pueden crearse en aplicaciones basadas en cuadros de diálogo.  Para obtener más información, vea [Tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md).  
  
## Personalizar cintas de opciones  
 Para abrir una cinta de opciones en el diseñador de la cinta de opciones, haga doble clic en el recurso de cinta de opciones en la vista de recursos.  En el diseñador, puede agregar, quitar y personalizar elementos de la cinta de opciones, el botón Aplicación o la barra de herramientas de acceso rápido.  También puede vincular eventos, por ejemplo, eventos de clic de botón y eventos de menú, a un método de la aplicación.  
  
 En la siguiente ilustración se muestran los distintos componentes del diseñador de la cinta de opciones.  
  
 ![Diseñador de la cinta de opciones de MFC](../mfc/media/ribbon_designer.png "Ribbon\_Designer")  
  
-   **Cuadro de herramientas:** contiene controles que se pueden arrastrar a la superficie del diseñador.  
  
-   **Superficie del diseñador:** contiene la representación visual del recurso de cinta de opciones.  
  
-   **Ventana Propiedades:** enumera los atributos del elemento seleccionado en la superficie del diseñador.  
  
-   **Ventana Vista de recursos:** muestra los recursos que incluyen recursos de cinta de opciones, en el proyecto.  
  
-   **Barra de herramientas Editor de Ribbon:** contiene comandos que permiten obtener una vista previa de la cinta de opciones y cambiar su tema visual.  
  
 Los temas siguientes describen cómo usar las características del diseñador de la cinta de opciones:  
  
-   [Cómo: Personalizar el botón Aplicación](../mfc/how-to-customize-the-application-button.md)  
  
-   [Cómo: Personalizar la barra de herramientas de acceso rápido](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
-   [Cómo: Agregar controles de cinta y controladores de eventos](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)  
  
-   [Cómo: Cargar un recurso de cinta desde una aplicación MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)  
  
## Definiciones de elementos de la cinta de opciones  
 ![Cinta de opciones de MFC](../mfc/media/ribbon.png "Ribbon")  
  
-   **Botón Aplicación:** botón que aparece en la esquina superior izquierda de una cinta de opciones.  El botón Aplicación reemplaza al menú Archivo y está visible incluso cuando se minimiza la cinta de opciones.  Al hacer clic en el botón, se muestra un menú con una lista de comandos.  
  
-   **Barra de herramientas de acceso rápido:** pequeña barra de herramientas personalizable que muestra comandos usados con frecuencia.  
  
-   **Categoría**: agrupamiento lógico que representa el contenido de una pestaña de la cinta de opciones.  
  
-   **Botón Categoría predeterminada:** botón que aparece en la cinta de opciones al minimizarla.  Al hacer clic en el botón, la categoría vuelve a aparecer como un menú.  
  
-   **Panel:** área de la barra de la cinta de opciones que muestra un grupo de controles relacionados.  Cada categoría de la cinta de opciones contiene uno o más paneles de cinta de opciones.  
  
-   **Elementos de la cinta de opciones:** controles de los paneles, por ejemplo, botones y cuadros combinados.  Para ver los distintos controles que se pueden hospedar en una cinta de opciones, vea [Ejemplo RibbonGadgets: aplicación de gadgets de la cinta de opciones](../top/visual-cpp-samples.md).  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)