---
title: Agregar funcionalidad con los asistentes para código (C++)
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.classes
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: 87c46be17c20bf9d592dd2b5c537897fa629e9c2
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "57822579"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Agregar funcionalidad con los asistentes para código (C++)

Una vez haya creado un proyecto, le interesará cambiar o ampliar su funcionalidad. Estas tareas incluyen crear clases, agregar funciones miembro y variables nuevas, y agregar métodos y propiedades de automatización. Los asistentes para código están diseñados para permitir hacer todo esto.

> [!WARNING]
> Varios asistentes de código de ATL y MFC han quedado en desuso y se quitarán en una versión futura de Visual Studio. Estos asistentes se usan con poca frecuencia. La compatibilidad general con ATL y MFC no se ve afectada por la eliminación de estos asistentes. Si quiere compartir sus comentarios sobre este desuso, rellene [esta encuesta](https://www.surveymonkey.com/r/QDWKKCN). Su opinión es importante para nosotros.

> [!NOTE]
>  Ahora, mediante la [ventana Propiedades](/visualstudio/ide/reference/properties-window), se pueden agregar controladores de mensajes y asignarles mensajes, y reemplazar funciones virtuales de MFC.

## <a name="accessing-visual-c-code-wizards"></a>Acceder a los asistentes para código de Visual C++

Hay tres ubicaciones desde las que se puede acceder a los asistentes para código de Visual C++:

- En el menú **Proyecto**, el comando **Agregar nuevo elemento** permite mostrar el cuadro de diálogo `Add New Item`, que sirve para agregar archivos nuevos al proyecto. El comando **Agregar clase** muestra el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), que a su vez abre asistentes para cada uno de los tipos de clase que se pueden agregar al proyecto. El comando **Agregar recurso** muestra el cuadro de diálogo [Agregar recurso](../windows/add-resource-dialog-box.md), desde el que se puede crear o seleccionar un recurso para agregarlo al proyecto.

   Si resalta una clase o interfaz del proyecto en la Vista de clases, en el menú **Proyecto** también se muestran los comandos siguientes:

   - **Implementar interfaz** (solo desde una clase de control).

   - **Agregar función**.

   - **Agregar variable**.

   - **Agregar punto de conexión** (solo para clases de ATL).

   - **Agregar método** (solo desde una interfaz).

   - **Agregar propiedad** (solo desde una interfaz).

   - **Agregar evento** (solo desde una clase de control).

- En el **Explorador de soluciones**, haga clic con el botón derecho en cualquier carpeta y haga clic en **Agregar** desde el menú contextual para agregar archivos nuevos o existentes, más carpetas, elementos, clases, recursos y referencias web al proyecto.

- Desde la [ventana Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón derecho en el nodo adecuado y haga clic en **Agregar** en el menú contextual para agregar funciones, variables, clases, propiedades, métodos, eventos, interfaces, puntos de conexión u otro código al proyecto.

   > [!NOTE]
   > Visual Studio no proporciona un asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o a [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) mediante la adición de un objeto simple con el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:

    ```IDL
    interface IMyInterface {
    };
    ```

   Vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar controles y objetos a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.

   |Acceder al asistente para código desde|Descripción|
   |-----------------------------|-----------------|
   |Agregar nuevo elemento|Los asistentes para código Agregar nuevo elemento agregan archivos de código fuente al proyecto. Si es necesario, se crean directorios adicionales para contener los archivos donde el motor de compilación de proyecto espera encontrarlos. Los asistentes para código disponibles desde el icono Agregar elemento incluyen los siguientes:<br /><br />- Agregar archivos de código fuente de C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />- Agregar archivos de desarrollo web (.html, .asp, .css, .xml).<br />- Agregar archivos de recursos y de utilidad (.bmp, .cur, .ico, .rct, .sql, .txt).<br /><br />Por lo general, estos asistentes para código no solicitan información, sino que agregan un archivo al árbol de desarrollo. Se puede cambiar el nombre del archivo en la ventana Propiedades.|
   |Explorador de soluciones|Los asistentes para código disponibles en el Explorador de soluciones dependen de dónde esté el foco del cursor al hacer clic con el botón derecho en un elemento. Si al hacer clic con el botón derecho en un elemento no aparece la opción **Agregar**, suba el cursor un nivel en el árbol de desarrollo e inténtelo de nuevo. Los asistentes para código siempre colocan el código adicional en el lugar adecuado en el árbol de desarrollo, con independencia de la posición del cursor. Los asistentes para código disponibles desde el Explorador de soluciones incluyen los siguientes:<br /><br />- Agregar clase (abre el cuadro de diálogo **Agregar clase** que contiene los asistentes para código nuevos).<br />- Agregar recurso (Nuevo, Importar o Personalizar).<br />- Agregar referencia web.|
   |Vista de clases|Los asistentes para código disponibles desde la Vista de clases dependen de dónde esté el foco del cursor al hacer clic con el botón derecho en un elemento. Si al hacer clic con el botón derecho en un elemento no aparece la opción **Agregar**, suba el cursor un nivel en el árbol de clases e inténtelo de nuevo. Los asistentes para código siempre colocan el código adicional en el lugar adecuado en el árbol de desarrollo, con independencia de la posición del cursor. Los asistentes para código disponibles en la Vista de clases incluyen los siguientes:<br /><br />- [Agregar funciones miembro](../ide/adding-a-member-function-visual-cpp.md).<br />- [Agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Agregar clases](../ide/adding-a-class-visual-cpp.md).<br />- [Implementar interfaz](../ide/implement-interface-wizard.md) (solo desde una clase de control).<br />- [Agregar punto de conexión](../ide/implement-connection-point-wizard.md) (solo para clases de ATL).<br />- [Agregar método](../ide/add-method-wizard.md) (solo desde una interfaz).<br />- [Agregar propiedad](../ide/names-add-property-wizard.md) (solo desde una interfaz).<br />- [Agregar evento](../ide/add-event-wizard.md) (solo desde una clase de control).<br /><br />Al seleccionar Agregar clase se abre el cuadro de diálogo **Agregar clase**, que proporciona acceso a todos los asistentes para código Agregar clase nuevos.|

## <a name="see-also"></a>Vea también

[Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)<br>
[Tipos de proyecto de Visual C++](../build/reference/visual-cpp-project-types.md)<br>
[Tipos de archivos creados para proyectos de Visual C++](../build/reference/file-types-created-for-visual-cpp-projects.md)
