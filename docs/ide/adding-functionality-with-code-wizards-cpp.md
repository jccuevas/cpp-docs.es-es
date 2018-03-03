---
title: "Agregar funcionalidad con los asistentes para código (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes
dev_langs:
- C++
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c27aeb10a58c828b6503ce96ddaadf138c258f27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-with-code-wizards-c"></a>Agregar funcionalidad con los asistentes para código (C++)
Una vez haya creado un proyecto, desea cambiar o agregar a la funcionalidad de ese proyecto. Estas tareas incluyen la creación de nuevas clases, agregar nuevas funciones miembro y variables y agregar métodos de automatización y propiedades. Los asistentes de código están diseñados para permitir hacer todas estas cosas.  
  
> [!NOTE]
>  Ahora puede agregar controladores de mensajes y asignarles mensajes y reemplazar funciones virtuales MFC mediante el [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
## <a name="accessing-visual-c-code-wizards"></a>Obtener acceso a los asistentes de código de Visual C++  
 Hay tres ubicaciones donde se pueden tener acceso a los asistentes para código de Visual C++:  
  
-   En el **proyecto** menú, el **Agregar nuevo elemento** comando le permite mostrar el `Add New Item` cuadro de diálogo que le servirá para agregar nuevos archivos al proyecto. El **Agregar clase** comando muestra el [Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo, que a su vez abre asistentes para cada uno de la clase de tipos que se puede agregar al proyecto. El **Agregar recurso** comando muestra el [Agregar recurso](../windows/add-resource-dialog-box.md) cuadro de diálogo, desde el que puede crear o seleccionar un recurso para agregarlo al proyecto.  
  
     Si resalta una clase o una interfaz en el proyecto en la vista de clases, el **proyecto** menú también muestra los siguientes comandos:  
  
    -   **Implementar interfaz** (de solo una clase de control)  
  
    -   **Add (función)**  
  
    -   **Agregar Variable**  
  
    -   **Agregar punto de conexión** (sólo en la clase ATL)  
  
    -   **El método Add** (sólo desde una interfaz)  
  
    -   **Agregar propiedad** (sólo desde una interfaz)  
  
    -   **Agregar evento** (de solo una clase de control)  
  
-   En **el Explorador de soluciones**, clic en cualquier carpeta y haga clic en **agregar** desde el acceso directo del menú le permite agregar archivos nuevos o existentes, más carpetas, elementos, clases, recursos y referencias Web para el proyecto.  
  
-   Desde el [ventana Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), con el botón secundario el nodo adecuado y haga clic en **agregar** desde el acceso directo del menú le permite agregar funciones, variables, clases, propiedades, métodos, eventos, interfaces, puntos de conexión, u otro código a su proyecto.  
  
    > [!NOTE]
    >  Visual Studio no proporciona un Asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o a un [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) mediante la adición de un objeto simple mediante el [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     Vea [implementando una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.  
  
    |Asistente para tener acceso al código desde|Descripción|  
    |-----------------------------|-----------------|  
    |Agregar nuevo elemento|Los asistentes para código Agregar nuevo elemento agregan archivos de código fuente al proyecto. Si es necesario, se crean directorios adicionales para que contenga los archivos donde se espera el motor de compilación de proyecto para encontrarlos. Asistentes para código disponibles desde el icono Agregar elemento incluyen:<br /><br /> -Agregar archivos de código fuente de C++ (.cpp,. h, .idl, .rc, .srf, .def, .rgs).<br />-Agregar archivos de desarrollo de Web (.html, .asp, .css, .xml).<br />-Agregar archivos de recursos y de utilidad (.bmp, .cur, .ico, .rct,. SQL, .txt).<br /><br /> Por lo general, estos asistentes para código no pedirán toda la información pero agregar un archivo en el árbol de desarrollo. Puede cambiar el nombre del archivo en la ventana Propiedades.|  
    |Explorador de soluciones|Los asistentes de código disponibles en el Explorador de soluciones dependen de que el foco del cursor es cuando se hace doble clic en un elemento. Si el **agregar** opción no aparece cuando hace clic en un elemento, mueva el cursor Subir un nivel en el árbol de desarrollo e inténtelo de nuevo. Los asistentes para código siempre colocará el código adicional en el lugar adecuado en el árbol de desarrollo, sin importar donde está el cursor. Asistentes para código disponibles desde el Explorador de soluciones incluyen:<br /><br /> -Agregar clase (abre la **Agregar clase** cuadro de diálogo que contiene los nuevos asistentes para código).<br />-Agregar recurso (nuevo, importar o personalizado).<br />-Agregar referencia Web.|  
    |Vista de clases|Los asistentes de código disponibles en la vista de clases dependen donde el foco del cursor es cuando haga clic en un elemento. Si el **agregar** opción no aparece cuando se haga clic en un elemento, mueva el cursor Subir un nivel en el árbol de clases e inténtelo de nuevo. Los asistentes para código siempre colocará el código adicional en el lugar adecuado en el árbol de desarrollo, sin importar donde está el cursor. Asistentes para código disponibles en la vista de clases se incluyen:<br /><br /> -   [Agregar la función miembro](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Agregar clase](../ide/adding-a-class-visual-cpp.md).<br />-   [Implementar interfaz](../ide/implement-interface-wizard.md) (de solo una clase de control)<br />-   [Agregar punto de conexión](../ide/implement-connection-point-wizard.md) (sólo en la clase ATL)<br />-   [El método Add](../ide/add-method-wizard.md) (sólo desde una interfaz)<br />-   [Agregar propiedad](../ide/names-add-property-wizard.md) (sólo desde una interfaz)<br />-   [Agregar evento](../ide/add-event-wizard.md) (de solo una clase de control)<br /><br /> Al seleccionar Agregar clase se abre el **Agregar clase** cuadro de diálogo que le da acceso a todos los nuevos asistentes para código Agregar clase.|  
  
## <a name="see-also"></a>Vea también  
 [Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)   
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)