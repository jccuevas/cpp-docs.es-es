---
title: "Agregar funcionalidad con los Asistentes para c&#243;digo | Microsoft Docs"
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
  - "vc.codewiz.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para clases [C++]"
  - "asistentes para código [C++]"
  - "proyectos [C++], agregar funcionalidad"
  - "proyectos de Visual C++, agregar funcionalidad"
  - "asistentes [C++], código"
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar funcionalidad con los Asistentes para c&#243;digo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez creado un proyecto, resulta conveniente cambiar la funcionalidad del proyecto o agregarle nueva funcionalidad.  Tales tareas incluyen crear nuevas clases, agregar nuevas funciones y variables miembro y agregar métodos y propiedades de automatización.  Los asistentes de código están diseñados para ayudarle a hacer todo esto.  
  
> [!NOTE]
>  Ahora puede agregar nuevos controladores de mensajes, asignarles mensajes y reemplazar funciones virtuales MFC mediante la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
## Obtener acceso a los Asistentes para código de Visual C\+\+  
 Hay tres ubicaciones donde se puede obtener acceso a los asistentes para código de Visual C\+\+:  
  
-   En el menú **Proyecto**, el comando **Agregar nuevo elemento** permite abrir el cuadro de diálogo `Add New Item`, que a su vez permite agregar nuevos archivos al proyecto.  El comando **Agregar clase** muestra el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), que a su vez abre asistentes por cada uno de los tipos de clase que esté agregando al proyecto.  El comando **Agregar recurso** muestra el cuadro de diálogo [Agregar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), en el que se puede crear o seleccionar un recurso para agregarlo al proyecto.  
  
     Si resalta una clase o una interfaz del proyecto en la Vista de clases, el menú **Proyecto** también muestra los siguientes comandos:  
  
    -   **Implementar interfaz** \(sólo desde una clase de control\)  
  
    -   **Agregar función**  
  
    -   **Agregar variable**  
  
    -   **Agregar punto de conexión** \(sólo en una clase ATL\)  
  
    -   **Agregar método** \(sólo desde una interfaz\)  
  
    -   **Agregar propiedad** \(sólo desde una interfaz\)  
  
    -   **Agregar evento** \(sólo desde una clase de control\)  
  
-   En el **Explorador de soluciones**, al hacer clic con el botón secundario del mouse en cualquier carpeta y seleccionar **Agregar** en el menú contextual se pueden agregar archivos nuevos o existentes, más carpetas, elementos, clases, recursos y referencias Web al proyecto.  
  
-   En la [ventana Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), al hacer clic con el botón secundario del mouse en el nodo correspondiente y seleccionar **Agregar** en el menú contextual se pueden agregar funciones, variables, clases, propiedades, métodos, eventos, interfaces, puntos de conexión o cualquier otro tipo de código al proyecto.  
  
    > [!NOTE]
    >  Visual Studio no proporciona un asistente para agregar una interfaz a un proyecto.  Se puede agregar una interfaz a un proyecto ATL o [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) agregando un objeto simple mediante el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md).  Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     Vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.  
  
    |Acceso al asistente para código desde|Descripción|  
    |-------------------------------------------|-----------------|  
    |Agregar nuevo elemento|Los asistentes para código Agregar nuevo elemento agregan archivos de código fuente al proyecto.  Si es necesario, se crean directorios adicionales que contendrán los archivos donde el motor de compilación del proyecto espera encontrarlos.  Los asistentes para código disponibles desde el icono Agregar elemento comprenden:<br /><br /> -   Agregue los archivos de código fuente de C\+\+ \(.cpp, .h, .idl, .rc, .srf, .def, .rgs\).<br />-   Agregue los archivos de desarrollo de web \(.html, .asp, .css, .xml\).<br />-   Agregue los archivos de recursos y de utilidad \(.bmp, .cur, .ico, .rct, .sql, .txt\).<br /><br /> Estos asistentes para código normalmente no piden ninguna información, sino que agregan un archivo al árbol de desarrollo.  Se puede cambiar el nombre de un archivo en la ventana Propiedades.|  
    |Explorador de soluciones|Los asistentes para código disponibles en el Explorador de soluciones dependen de dónde se halle el foco del cursor al hacer clic con el botón secundario del mouse en un elemento.  Si la opción **Agregar** no aparece al hacer clic con el botón secundario del mouse en un elemento, mueva el cursor un nivel hacia arriba en el árbol de desarrollo e inténtelo de nuevo.  Los Asistentes para código siempre colocarán el código adicional en el lugar adecuado del árbol de desarrollo, sin importar dónde se halle el cursor.  Los asistentes para código disponibles en el Explorador de soluciones comprenden:<br /><br /> -   Agregar clase \(abre el cuadro de diálogo **Agregar clase** que contiene los nuevos asistentes para código\).<br />-   Agregar recurso \(Nuevo, Importar o Personalizado\).<br />-   Agregar referencia web.|  
    |Vista de clases|Los asistentes para código disponibles en la Vista de clases dependen de dónde se halle el foco del cursor al hacer clic con el botón secundario del mouse en un elemento.  Si la opción **Agregar** no aparece al hacer clic con el botón secundario del mouse en un elemento, mueva el cursor un nivel hacia arriba en el árbol de clases e inténtelo de nuevo.  Los Asistentes para código siempre colocarán el código adicional en el lugar adecuado del árbol de desarrollo, sin importar dónde se halle el cursor.  Los asistentes para código disponibles en la Vista de clases comprenden:<br /><br /> -   [Asistente para agregar funciones miembro](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Agregar clase \(cuadro de diálogo\)](../ide/adding-a-class-visual-cpp.md).<br />-   [Implementar interfaz](../ide/implement-interface-wizard.md) \(solo desde una clase de control\)<br />-   [Agregar punto de conexión](../ide/implement-connection-point-wizard.md) \(sólo en una clase ATL\)<br />-   [Agregar método](../ide/add-method-wizard.md) \(sólo desde una interfaz\)<br />-   [Agregar propiedad](../ide/names-add-property-wizard.md) \(sólo desde una interfaz\)<br />-   [Agregar evento](../ide/add-event-wizard.md) \(sólo desde una clase de control\)<br /><br /> Al seleccionar Agregar clase se abre el cuadro de diálogo del mismo nombre, que da acceso a todos los nuevos asistentes para código Agregar clase.|  
  
## Vea también  
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Explorar la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Tipos de proyecto de Visual C\+\+](../ide/visual-cpp-project-types.md)   
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)