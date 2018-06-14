---
title: Agregar funcionalidad con los asistentes para código (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55a2bb282d19a48cfd510056e327e7abca4de4ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337046"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Agregar funcionalidad con los asistentes para código (C++)
Una vez haya creado un proyecto, le interesará cambiar o ampliar su funcionalidad. Estas tareas incluyen crear clases, agregar funciones miembro y variables nuevas, y agregar métodos y propiedades de automatización. Los asistentes para código están diseñados para permitir hacer todo esto.  
  
> [!NOTE]
>  Ahora, mediante la [ventana Propiedades](/visualstudio/ide/reference/properties-window), se pueden agregar controladores de mensajes y asignarles mensajes, y reemplazar funciones virtuales de MFC.  
  
## <a name="accessing-visual-c-code-wizards"></a>Acceder a los asistentes para código de Visual C++  
 Hay tres ubicaciones desde las que se puede acceder a los asistentes para código de Visual C++:  
  
-   En el menú **Proyecto**, el comando **Agregar nuevo elemento** permite mostrar el cuadro de diálogo `Add New Item`, que sirve para agregar archivos nuevos al proyecto. El comando **Agregar clase** muestra el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), que a su vez abre asistentes para cada uno de los tipos de clase que se pueden agregar al proyecto. El comando **Agregar recurso** muestra el cuadro de diálogo [Agregar recurso](../windows/add-resource-dialog-box.md), desde el que se puede crear o seleccionar un recurso para agregarlo al proyecto.  
  
     Si resalta una clase o interfaz del proyecto en la Vista de clases, en el menú **Proyecto** también se muestran los comandos siguientes:  
  
    -   **Implementar interfaz** (solo desde una clase de control).  
  
    -   **Agregar función**.  
  
    -   **Agregar variable**.  
  
    -   **Agregar punto de conexión** (solo para clases de ATL).  
  
    -   **Agregar método** (solo desde una interfaz).  
  
    -   **Agregar propiedad** (solo desde una interfaz).  
  
    -   **Agregar evento** (solo desde una clase de control).  
  
-   En el **Explorador de soluciones**, haga clic con el botón derecho en cualquier carpeta y haga clic en **Agregar** desde el menú contextual para agregar archivos nuevos o existentes, más carpetas, elementos, clases, recursos y referencias web al proyecto.  
  
-   Desde la [ventana Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón derecho en el nodo adecuado y haga clic en **Agregar** en el menú contextual para agregar funciones, variables, clases, propiedades, métodos, eventos, interfaces, puntos de conexión u otro código al proyecto.  
  
    > [!NOTE]
    >  Visual Studio no proporciona un asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o a [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) mediante la adición de un objeto simple con el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     Vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar controles y objetos a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.  
  
    |Acceder al asistente para código desde|Description|  
    |-----------------------------|-----------------|  
    |Agregar nuevo elemento|Los asistentes para código Agregar nuevo elemento agregan archivos de código fuente al proyecto. Si es necesario, se crean directorios adicionales para contener los archivos donde el motor de compilación de proyecto espera encontrarlos. Los asistentes para código disponibles desde el icono Agregar elemento incluyen los siguientes:<br /><br /> -    Agregar archivos de código fuente de C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />-   Agregar archivos de desarrollo web (.html, .asp, .css, .xml).<br />-   Agregar archivos de recursos y de utilidad (.bmp, .cur, .ico, .rct, .sql, .txt).<br /><br /> Por lo general, estos asistentes para código no solicitan información, sino que agregan un archivo al árbol de desarrollo. Se puede cambiar el nombre del archivo en la ventana Propiedades.|  
    |Explorador de soluciones|Los asistentes para código disponibles en el Explorador de soluciones dependen de dónde esté el foco del cursor al hacer clic con el botón derecho en un elemento. Si al hacer clic con el botón derecho en un elemento no aparece la opción **Agregar**, suba el cursor un nivel en el árbol de desarrollo e inténtelo de nuevo. Los asistentes para código siempre colocan el código adicional en el lugar adecuado en el árbol de desarrollo, con independencia de la posición del cursor. Los asistentes para código disponibles desde el Explorador de soluciones incluyen los siguientes:<br /><br /> -   Agregar clase (abre el cuadro de diálogo **Agregar clase** que contiene los asistentes para código nuevos).<br />-   Agregar recurso (Nuevo, Importar o Personalizar).<br />-   Agregar referencia web.|  
    |Vista de clases|Los asistentes para código disponibles desde la Vista de clases dependen de dónde esté el foco del cursor al hacer clic con el botón derecho en un elemento. Si al hacer clic con el botón derecho en un elemento no aparece la opción **Agregar**, suba el cursor un nivel en el árbol de clases e inténtelo de nuevo. Los asistentes para código siempre colocan el código adicional en el lugar adecuado en el árbol de desarrollo, con independencia de la posición del cursor. Los asistentes para código disponibles en la Vista de clases incluyen los siguientes:<br /><br /> -   [Agregar funciones miembro](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Agregar clases](../ide/adding-a-class-visual-cpp.md).<br />-   [Implementar interfaz](../ide/implement-interface-wizard.md) (solo desde una clase de control).<br />-   [Agregar punto de conexión](../ide/implement-connection-point-wizard.md) (solo para clases de ATL).<br />-   [Agregar método](../ide/add-method-wizard.md) (solo desde una interfaz).<br />-   [Agregar propiedad](../ide/names-add-property-wizard.md) (solo desde una interfaz).<br />-   [Agregar evento](../ide/add-event-wizard.md) (solo desde una clase de control).<br /><br /> Al seleccionar Agregar clase se abre el cuadro de diálogo **Agregar clase**, que proporciona acceso a todos los asistentes para código Agregar clase nuevos.|  
  
## <a name="see-also"></a>Vea también  
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)   
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)