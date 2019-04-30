---
title: Procedimiento Creación de recursos (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: c22df99240c0fa076124e33224a4f6f4ab9a957e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376831"
---
# <a name="how-to-create-resources-c"></a>Procedimiento Creación de recursos (C++)

Puede crear recursos para su proyecto:

- Uso de un archivo de script de recursos.

   > [!NOTE]
   > Este paso es necesario antes de agregar los recursos.

- Agregar recursos a su proyecto y utilizar el **vista de recursos**.

- Uso de una plantilla de recursos para crear recursos personalizados.

## <a name="use-resource-script-files"></a>Usar archivos de Script de recursos

Antes de crear y agregar nuevos recursos al proyecto, primero debe crear un archivo de recursos (.rc) de la secuencia de comandos.

> [!NOTE]
> Solo se puede agregar un archivo de script de recursos a un proyecto existente que se cargan en el IDE de Visual Studio. No se puede crear un script de recursos independiente fuera del proyecto, aunque se pueden crear archivos de recursos (.rct) de la plantilla en cualquier momento.

### <a name="to-create-a-resource-script-file"></a>Para crear un archivo de script de recursos

1. Coloca el foco en la carpeta del proyecto existente en **el Explorador de soluciones**, por ejemplo, *MyProject*.

   > [!NOTE]
   > No confunda la carpeta del proyecto con la carpeta de soluciones en **el Explorador de soluciones**. Si coloca el foco en el **solución** carpeta, no tienen el mismo **Agregar nuevo elemento** opciones.

1. En el menú, vaya a **proyecto** > **Agregar nuevo elemento**.

1. Seleccione el **Visual C++** carpeta y elija **archivo de recursos (.rc)** en el panel derecho.

1. Proporcione un nombre para el archivo de script de recursos en el **nombre** cuadro de texto y seleccione **abierto**.

### <a name="to-open-a-resource-script-file"></a>Para abrir un archivo de script de recursos

Puede ver los recursos en un archivo de script de recursos sin tener un proyecto abierto. Se abre el archivo de script en una ventana de documento en contraposición a la **vista de recursos**.

> [!NOTE]
> Algunos comandos solo están disponibles si el archivo se abre de forma independiente, lo que significa que fuera de un proyecto sin cargar primero el proyecto. Por ejemplo, para usar el **Guardar como** comando y guardar un archivo con un formato diferente o un nombre de archivo, el archivo debe ser abre de forma independiente.

- Para abrir un archivo de script de recursos fuera de un proyecto, en el menú, vaya a **archivo** > **abrir**y elija **archivo**. Navegue hasta el archivo de script de recursos, resalte el archivo y elija **abierto**.

    > [!NOTE]
    > Puede haber ocasiones cuando desee ver el contenido del archivo de script de recursos del proyecto sin usar los editores de recursos para abrir un recurso. Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente. Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos que contiene y realizar operaciones globales admitidas por el editor de texto.
    >
    > Para abrir un archivo de script de recursos en formato de texto, use la flecha de lista desplegable en el lado derecho de la **abrir** situado en el paso anterior y elija **abrir con**. Seleccione **Editor de código fuente (texto)** y desde el **abrir como** lista desplegable, seleccione **texto** y el recurso se abrirá en el **código fuente** Editor.

- Para abrir el recurso de varias secuencias de comandos siguen el mismo paso anterior para cada archivo que desea abrir, por ejemplo, *Source1.RF* y *Source2.rc*. A continuación, cuando los archivos .rc estén abiertos en ventanas de documentos independientes, o bien utilice el **ventana** menú o haga clic en uno de los archivos y elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical** . Ahora se organizan en mosaico las ventanas para que pueda ver al mismo tiempo.

> [!TIP]
> Puede abrir los archivos de script de recursos haciendo clic con el archivo .rc en **el Explorador de soluciones**, seleccionar **abrir con** y eligiendo **Editor de código fuente (texto)**.

Al compilar una aplicación de Microsoft Foundation Class (MFC) para el uso de Windows la [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos, incluido un archivo de recursos (.rc) de la secuencia de comandos) que contiene las características principales de MFC. Sin embargo, estas características específicas de MFC no están disponibles al editar un archivo .rc para aplicaciones de Windows no basada en MFC. Esto incluye los asistentes para código, las cadenas de mensajes de menú, mostrar el contenido de los controles de cuadro combinado y hospedaje de controles ActiveX.

- Para agregar compatibilidad con MFC, con el archivo de script de recursos abierto, en **vista de recursos**, resalte la carpeta de recursos (por ejemplo, *MFC.rc*). A continuación, en el [ventana propiedades](/visualstudio/ide/reference/properties-window), establezca **MFC Mode** a **True**.

  > [!NOTE]
  > Además de establecer **MFC Mode**, el archivo .rc deberá formar parte de un proyecto MFC. Solo configuración **MFC Mode** a **True** en un .rc archivo en un proyecto de Win32 no le ofrecerán las características de MFC.

## <a name="create-resources"></a>Creación de recursos

Puede crear un recurso como un nuevo recurso de forma predeterminada, lo que significa que un recurso que no se basa en una plantilla o como un recurso basado en una plantilla.

Use la **vista de recursos** ventana para mostrar los archivos de recursos incluidos en los proyectos. Al expandir la carpeta principales, por ejemplo, *Project1.rc*, muestra los tipos de recursos dentro de ese archivo. Expanda cada tipo de recurso para mostrar los recursos individuales de ese tipo.

> [!TIP]
> Para abrir el **vista de recursos** ventana, vaya al menú **vista** > **vista de recursos** o presione **Ctrl** +  **MAYÚS**+**E**.

También puede usar el botón secundario en el **vista de recursos** ventana para iniciar un menú contextual de comandos o haga doble clic en la barra de título para acoplar y desacoplar la ventana. Haga clic en la barra de título para los comandos que controlan el comportamiento de la ventana. Para obtener más información, consulte [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

El **vista de recursos** windows incluye el **Agregar recurso** cuadro de diálogo con las siguientes propiedades para agregar recursos a un proyecto de aplicación de escritorio de Windows de C++:

| Propiedad | Descripción |
|---|---|
| **Tipo de recurso** | Especifique el tipo de recurso que desea crear.<br/><br/>Puede expandir las categorías de recursos de cuadro de cursor y el cuadro de diálogo para mostrar otros recursos, que se encuentran en *... \Microsoft visual Studio \<versión\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct*. Si necesita agregar archivos .rct, colocarlos aquí o especificar otro [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md). Recursos que se muestran en el nivel superior en el control de árbol son los recursos predeterminados suministrados por Visual Studio. Los recursos en archivos .rct aparecen en el segundo nivel bajo la categoría apropiada. No hay ningún límite preestablecido respecto al número de archivos .rct que puede agregar.<br/><br/> |
| **Nuevo** | Crear un recurso en función del tipo seleccionado en el **tipo de recurso** cuadro y abra el recurso en el editor adecuado.<br/><br/>Por ejemplo, si crea un recurso de cuadro de diálogo, abre el recurso en el [Editor de cuadro de diálogo](../windows/dialog-editor.md). |
| **Import** | Abra el **importar** cuadro de diálogo para navegar hasta el recurso que desea importar en el proyecto actual.<br/><br/>Puede importar un mapa de bits, icono, cursor, HTML, sonido (. WAV), o el archivo de recursos personalizados. |
| **Custom** | Abra el **nuevo recurso personalizado** cuadro de diálogo para crear un recurso personalizado.<br/><br/>También incluye un **tipo de recurso** propiedad que proporciona un cuadro de texto para escribir el nombre del tipo de recurso personalizado. Visual C++ aprovecha automáticamente el nombre al salir. Recursos personalizados sólo se editan en el [Editor binario](../windows/binary-editor.md). |

Cuando se crea un nuevo recurso, Visual C++ le asigna un nombre único, por ejemplo, `IDD_Dialog1`. Puede personalizar este identificador editando las propiedades del recurso en el editor de recursos asociado o en la [ventana propiedades](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> No especifique un nombre de recurso o un identificador que está reservado por Visual Studio. Nombres reservados son `DESIGNINFO`, `HWB`, y `TEXTINCLUDE`, y el identificador reservado es `255`.

### <a name="to-create-a-resource"></a>Para crear un recurso

- En **vista de recursos**, seleccione el archivo .rc y luego usar **editar** > **Agregar recurso** y elija el tipo de recurso que se agregará al proyecto.

   > [!TIP]
   > También puede haga clic en el archivo .rc en **vista de recursos** y elija **Agregar recurso** en el menú contextual.

- En **el Explorador de soluciones**, haga clic en la carpeta del proyecto, seleccione **agregar** > **Agregar recurso** y elija el tipo de recurso que se agregará al proyecto.

   > [!NOTE]
   > Si aún no tiene un archivo .rc en el proyecto, este paso creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.

- En [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en la clase, seleccione **agregar** > **Agregar recurso** y elija el tipo de recurso que se agregará al proyecto.

- Use el menú **proyecto** > **Agregar recurso**.

## <a name="use-resource-templates"></a>Usar plantillas de recursos

Una plantilla de recursos es un recurso personalizado que ha guardado como un archivo .rct. Una plantilla de recursos, a continuación, actúa como punto de partida para crear recursos. Las plantillas de recursos ahorran tiempo en el desarrollo de recursos adicionales o grupos de recursos que comparten características, como los controles estándar o repiten los elementos. Por ejemplo, si desea incluir un botón de ayuda con un icono del logotipo de empresa en varios cuadros de diálogo, cree una nueva plantilla de cuadro de diálogo y personalizarlo con el botón de ayuda y el logotipo.

Después de personalizar una plantilla de recursos, guardar los cambios en la carpeta de plantillas o en la ubicación especificada en la ruta de inclusión, para que aparezca bajo su tipo de recurso en el **Agregar recurso** cuadro de diálogo. Ahora puede usar la nueva plantilla de recursos tantas veces como sea necesario.

> [!NOTE]
> El editor de recursos proporciona automáticamente un identificador de recurso único. Puede revisar el [propiedades del recurso](../windows/changing-the-properties-of-a-resource.md) según sea necesario.

> [!NOTE]
> Coloque los archivos de plantilla específicos del idioma en subdirectorios del directorio principal de plantillas. Por ejemplo, los archivos de plantilla solo en inglés Ir *... \\< directorio de plantillas de recursos\>\1033*.
>
> Visual Studio busca nuevos archivos .rct en *\Program Files\Microsoft Visual Studio \<versión\>\VC\VCResourceTemplates*, *\Program Files\Microsoft Visual Studio \< versión > \VC\VCResourceTemplates\\< LCID\>*  (por ejemplo, un LCID 1033 para inglés), o en cualquier parte de la [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md). Si desea almacenar los archivos RCT en otra ubicación, debe agregar la ubicación a la ruta de inclusión.

### <a name="to-create-and-use-a-resource-template"></a>Para crear y usar una plantilla de recursos

1. En **el Explorador de soluciones**, haga clic en el proyecto y seleccione **agregar** > **Agregar nuevo elemento**.

1. En el **plantillas:** panel, seleccione **el archivo de plantilla de recursos (.rct)**.

1. Proporcione un nombre y ubicación para el nuevo *.rct* de archivo y elija **abierto**.

   El nuevo *.rct* archivo se agrega al proyecto y aparece en **el Explorador de soluciones** bajo el **recursos** carpeta.

1. Haga doble clic en el *.rct* archivo para abrirlo en una ventana de documento. Para agregar recursos, haga clic en el archivo en la ventana de documento y elija **Agregar recurso**.

   Puede personalizar los recursos se ha agregado y guardar el *.rct* archivo.

1. En el **vista de recursos** panel, haga clic en el *.rc* de archivo y elija **Agregar recurso**.

1. Seleccione el signo más (**+**) junto a un recurso para expandir el nodo de recursos y ver las plantillas disponibles para ese recurso.

1. Haga doble clic en la plantilla que desea editar.

   Puede modificar el recurso agregado según sea necesario en su editor de recursos.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Para convertir un archivo de recursos existente en una plantilla

Con el archivo de script de recursos abierto, en el menú, vaya a **archivo** > **guardar \< *filename*> como**. Especifique una ubicación y elija **Aceptar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: Administrar recursos](../windows/how-to-copy-resources.md)<br/>
[Cómo: Incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)<br/>