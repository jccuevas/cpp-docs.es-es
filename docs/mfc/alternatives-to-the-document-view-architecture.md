---
title: "Alternativas a la arquitectura documento/vista | Microsoft Docs"
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
  - "CDocument (clase), requisitos de espacio"
  - "documentos, aplicaciones sin"
  - "vistas, aplicaciones sin"
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Alternativas a la arquitectura documento/vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones MFC utilizan normalmente la arquitectura documento\/vista administrar información, los formatos de archivo, y la representación visual de los datos a los usuarios.  Para la mayoría de aplicaciones de escritorio, la arquitectura documento\/vista es una arquitectura adecuada y eficaz de la aplicación.  Esta arquitectura separa los datos de la vista y, en la mayoría de los casos, simplifica la aplicación y reduce código redundante.  
  
 Sin embargo, el documento o la arquitectura de la vista no está adecuados para algunas situaciones.  Considere estos ejemplos:  
  
-   Si el convertir una aplicación escrita en C para Windows, puede que desee completar el puerto poder agregar compatibilidad de documento y vista a la aplicación.  
  
-   Si está escribiendo una utilidad ligera, puede que puede hacer sin la arquitectura documento\/vista.  
  
-   Si el código original combinación ya la administración de datos con la vista de los datos, mueva el código al modelo de documento y vista no es digno de esfuerzo porque debe separar los dos.  Puede ser preferible dejar el código como está.  
  
 Para crear una aplicación que no utiliza la arquitectura documento\/vista, desactive la casilla de **Document\/View architecture support** en el paso 1 del Asistente para aplicaciones MFC.  Vea [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para obtener detalles.  
  
> [!NOTE]
>  Las aplicaciones Diálogo\- basadas generadas por el Asistente para aplicaciones MFC no utilizan la arquitectura documento\/vista, por lo que la casilla está desactivada de **Document\/View architecture support** si selecciona el tipo de aplicación del diálogo.  
  
 Los asistentes de Visual C\+\+, así como el origen y editores de cuadros de diálogo, trabajar con la aplicación generada igual que con cualquier otra aplicación Asistente\- generada.  La aplicación puede admitir las barras de herramientas, las barras de desplazamiento, y una barra de estado, y tiene un cuadro de **Acerca de** .  La aplicación no se registrará ningún plantillas de documento, y no contendrá una clase document.  
  
 Observe que la aplicación generada tiene una clase de vista, **CChildView**, derivado de `CWnd`.  MFC crea y las posiciones una instancia de la clase de vista dentro de las ventanas de marco creadas por la aplicación.  MFC todavía aplica utilizando una ventana de vista, porque simplifica la posición y administrar el contenido de la aplicación.  Puede agregar código de dibujo al miembro de `OnPaint` de esta clase.  El código debe agregar barras de desplazamiento a la vista en lugar del cuadro.  
  
 Dado que la arquitectura documento\/vista proporcionado por MFC es responsable de implementar muchas de las características de una aplicación, su ausencia en el proyecto significa que es responsable de implementar muchas características importantes de la aplicación:  
  
-   Suministrados por el asistente para aplicaciones MFC, el menú de la aplicación sólo contiene `New` y comandos de `Exit` en el menú de **archivo** . \(El comando `New` sólo se admite para las aplicaciones MDI, no las aplicaciones SDI sin compatibilidad de documento y vista.\) El recurso representado del menú no admitirá un MRU \(utilizado recientemente\) list.  
  
-   Debe agregar funciones y las implementaciones para los comandos que la aplicación admita, incluidos **Abierta** y **Guardar** de controlador en el menú de **archivo** .  MFC proporciona normalmente código admitir estas características, pero ese compatibilidad está enlazado estrechamente a la arquitectura documento\/vista.  
  
-   La barra de herramientas de la aplicación, si se solicita uno, se mínima.  
  
 Se recomienda encarecidamente utilizar el asistente para crear aplicaciones sin la arquitectura documento\/vista, porque el asistente garantiza una arquitectura correcta de MFC.  Sin embargo, si debe evitar utilizar el asistente, aquí se varios enfoques para omitir la arquitectura documento\/vista en el código:  
  
-   Tratar el documento como integrados no y aplique el código de administración de datos en la clase de vista, como sugerido anteriormente.  La sobrecarga del documento es relativamente baja.  Un único objeto de [CDocument](../mfc/reference/cdocument-class.md) incurre en una pequeña cantidad de único de arriba, más la pequeña sobrecarga de las clases base, de [CCmdTarget](../mfc/reference/ccmdtarget-class.md) y de [CObject](../mfc/reference/cobject-class.md)de **CDocument** .  Las dos últimas clases son pequeñas.  
  
     Declarado en **CDocument**:  
  
    -   Dos objetos de `CString` .  
  
    -   Tres s de **bool**.  
  
    -   Un puntero de `CDocTemplate` .  
  
    -   Un objeto de `CPtrList` , que contiene una lista de las vistas del documento.  
  
     Además, el documento requiere la cantidad de tiempo de crear el objeto document, los objetos de vista, una ventana de marco, y un objeto de plantilla de documento.  
  
-   Tratar el documento y vista como accesorios no usados.  Coloque el código de administración de datos y del gráfico en la ventana de marco en lugar de la vista.  Este enfoque está más cercano al modelo de programación del lenguaje C.  
  
-   Reemplace las partes del marco de trabajo de MFC que crean el documento y vista para eliminar crearlos en absoluto.  El proceso de creación de documentos se inicia con una llamada a `CWinApp::AddDocTemplate`.  Elimine la llamada de la función miembro de `InitInstance` de la clase de aplicación y, en su lugar, cree una ventana en `InitInstance` personalmente de marco.  Coloque el código de administración de datos en la clase de ventana de marco.  El proceso de creación de documento y vista se muestra en [Creación de documentos y vistas](../mfc/document-view-creation.md).  Es más trabajo y requiere conocimientos más profunda de marco, pero se libera completamente de sobrecarga de documento y vista.  
  
 El artículo [MFC: Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md) proporciona ejemplos más concretos de las alternativas de documentos y vistas en el contexto de aplicaciones de base de datos.  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)