---
title: Filtrar Creación de recursos (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 5a0bc6370d0973d63eb16ac992251531aa2e5193
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152396"
---
# <a name="how-to-create-resources-c"></a>Filtrar Creación de recursos (C++)

> [!NOTE]
> El **Editor de recursos** o **vista de recursos** no está disponible en las ediciones Express.
>
> Esta información no se aplica a los recursos en aplicaciones de escritorio de Windows o aplicaciones de la plataforma Universal de Windows. Proyectos en lenguajes .NET no usan archivos de script de recursos. Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [archivos de recursos](../windows/resource-files-visual-studio.md), [recursos de la aplicación y el sistema de administración de recursos](/windows/uwp/app-resources/), y [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="create-a-resource-script"></a>Crear un script de recursos

Antes de crear y agregar nuevos recursos al proyecto, primero debe crear un script de recursos (archivo .rc).

> [!NOTE]
> Solo se puede agregar un script de recursos (archivo .rc) a un proyecto existente que esté cargado en el IDE de Visual Studio. No se puede crear un script de recursos independiente (fuera del proyecto). Las plantillas de recursos (archivos .rct) pueden crearse en cualquier momento.

### <a name="to-create-a-resource-script"></a>Para crear un script de recursos

1. Coloca el foco en la carpeta del proyecto existente en **el Explorador de soluciones**, por ejemplo, *MyProject*.

   > [!NOTE]
   > No confunda la carpeta del proyecto con la carpeta de soluciones en **el Explorador de soluciones**. Si coloca el foco en el **solución** carpeta, sus elecciones en el **Agregar nuevo elemento** cuadro de diálogo será diferente.

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione el **Visual C++** a continuación, elija la carpeta **archivo de recursos (.rc)** en el panel derecho.

1. Proporcione un nombre para el script del recurso en el **nombre** texto cuadro y, después, seleccione **abierto**.

### <a name="to-open-a-resource-script"></a>Para abrir un script de recursos

Puede ver los recursos en un script de recursos sin tener un proyecto abierto. Se abrirá el archivo de script en una ventana de documento en lugar de abrirse en el **vista de recursos** ventana (como ocurre cuando el archivo se abre dentro de un proyecto).

> [!NOTE]
> Algunos comandos están disponibles solo cuando el archivo está abierto independiente (fuera de un proyecto). Abrir un archivo de independiente significa abrir sin cargar primero el proyecto.
>
> Por ejemplo, para guardar un archivo en un formato diferente o como un nombre de archivo diferente (como el **Guardar como** comando no está disponible para el archivo dentro de un proyecto). Si abre el proyecto primero mediante **archivo** > **abrir** > **proyecto**, estos comandos no están disponibles.

Para abrir un script de recursos fuera de un proyecto:

1. Desde el **archivo** menú, seleccione **abierto**, a continuación, elija **archivo**.

1. En el **abrir archivo** cuadro de diálogo, navegue hasta el archivo de script de recursos, resalte el archivo y elija **abierto**.

Para abrir varios scripts de recursos fuera de un proyecto:

1. Abra ambos archivos de recursos de manera independiente. Por ejemplo, abra *Source1.RF* y *Source2.rc*.

1. Desde el **archivo** menú, elija **abierto**, a continuación, seleccione **archivo**.

1. En el **abrir archivo** cuadro de diálogo, navegue hasta el primer archivo de script de recursos que desee abrir (*Source1.RF*), resalte el archivo y elija **abrir**.

1. Repita el paso anterior para abrir el segundo archivo .rc (*Source2.rc*).

   Los archivos .rc ahora están abiertos en ventanas de documentos independientes.

1. Cuando los archivos .rc estén abiertos en el **ventana** menú (o haga uno de los archivos .rc) elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical**.

   Ahora se organizan en mosaico las ventanas para que pueda ver al mismo tiempo.

Puede haber ocasiones en que desee ver el contenido del archivo de script de recursos (.rc) del proyecto sin abrir un recurso, como un cuadro de diálogo, en su editor de recursos específico. Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente.

Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos que contiene y realizar operaciones globales admitidas por el editor de texto.

> [!NOTE]
> Los editores de recursos no leen directamente .rc o `resource.h` archivos. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como en un proceso de compilación normal, la información que no es simbólica (por ejemplo, los comentarios) se descarta durante el proceso de compilación. Cada vez que el archivo .aps obtiene fuera de sincronización con el archivo .rc, se vuelve a generar el archivo .rc (por ejemplo, cuando se guarda, el editor de recursos sobrescribe el archivo .rc y `resource.h` archivo). Los cambios realizados en los propios recursos permanecen incorporados en el archivo .rc, pero los comentarios se pierden una vez que se sobrescribe el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

Para abrir un archivo de script de recursos en formato de texto:

1. Desde el **archivo** menú, seleccione **abierto**, a continuación, elija **archivo**.

1. En el **abrir archivo** cuadro de diálogo, navegue hasta el archivo de script de recursos que desea ver en formato de texto.

1. Resalte el archivo y luego seleccione la flecha desplegable en el **abierto** botón (en la parte derecha del botón).

1. Elija **abrir con** en el menú desplegable.

1. En el **abrir con** cuadro de diálogo, seleccione **Editor de código fuente (texto)**.

1. Desde el **abrir como** lista desplegable, seleccione **texto**.

   El recurso se abrirá en el **código fuente** editor.

> [!TIP]
> Es un acceso directo que hace clic en el archivo .rc en **el Explorador de soluciones**, elija **abrir con...**  y seleccione **Editor de código fuente (texto)**.

### <a name="to-add-mfc-support"></a>Para agregar compatibilidad con MFC

Normalmente, si se crea una aplicación de Microsoft Foundation Class (MFC) para el uso de Windows la [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos (como un archivo de recursos (.rc) de la secuencia de comandos) que contiene las características principales de la MFC. Sin embargo, al editar un archivo .rc para una aplicación de Windows no basada en MFC, las siguientes características MFC no están disponibles:

Algunas características específicas de MFC incluyen los asistentes para código MFC, cadenas de mensajes de menú, mostrar el contenido de los controles de cuadro combinado y hospedaje de controles ActiveX.

Para agregar compatibilidad con MFC a un archivo de script de recursos:

1. Abra el archivo de script de recursos.

1. En **vista de recursos**, resalte la carpeta de recursos (por ejemplo, *MFC.rc*).

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), establezca el **MFC Mode** propiedad **True**.

   > [!NOTE]
   > Además de establecer esta propiedad, el archivo .rc debe formar parte de un proyecto MFC. Por ejemplo, simplemente establecer **MFC Mode** a **True** en un .rc archivo en un proyecto de Win32 no le ofrecerán las características de MFC.

## <a name="create-a-resource"></a>Crear un recurso

Puede crear un recurso como recursos nuevos predeterminados (es decir, un recurso que no se basa en una plantilla) o como un recurso basado en una plantilla.

Cuando se crea un nuevo recurso, Visual C++ le asigna un nombre único, por ejemplo, `IDD_Dialog1`. Puede personalizar este identificador editando las propiedades del recurso en el editor de recursos asociado o en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> No especifique un nombre de recurso o un identificador que está reservado por Visual Studio. Nombres reservados son DESIGNINFO, HWB y TEXTINCLUDE y el identificador reservado es 255.

El **vista de recursos** ventana muestra los archivos de recursos incluidos en los proyectos. Al expandir la carpeta superior (por ejemplo, *Project1.rc*) muestra los tipos de recursos en que el archivo y expandir cada tipo de recurso muestra los recursos individuales de ese tipo.

> [!TIP]
> Para abrir la ventana de vista de recursos, seleccione **vista de recursos** en el **vista** menú (o use **Ctrl** + **MAYÚS**  +  **E**).
>
> Use haga doble clic en el **vista de recursos** ventana para iniciar un menú contextual de comandos o haga doble clic en la barra de título para acoplar o desacoplar la ventana. Haciendo clic en la barra de título proporciona comandos adicionales que le permiten controlar el comportamiento de la ventana. Para obtener más información, consulte [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Use la **Agregar recurso** cuadro de diálogo Agregar recursos a un proyecto de aplicación de escritorio de Windows de C++ con las siguientes propiedades:

|Property|Descripción|
|-|-|
|**Tipo de recurso**|Especifica el tipo de recurso que se desea crear.<br/><br/>Se pueden expandir las categorías de recursos de cursor y de cuadro de diálogo para mostrar otros recursos. Estos recursos están ubicados en ...\Microsoft Visual Studio \<versión\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si agrega archivos .rct, colocarlos en este directorio o especificar otro [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md). Los recursos de esos archivos aparecen en el segundo nivel de la categoría correspondiente. No hay ningún límite preestablecido respecto al número de archivos .rct que puede agregar.<br/><br/>Los recursos que se muestran en el nivel superior del control de árbol son los recursos predeterminados suministrados por Visual Studio.|
|**Nuevo**|Crea un recurso en función del tipo seleccionado en el **tipo de recurso** cuadro y abre el recurso en el editor adecuado. Por ejemplo, si crea un recurso de cuadro de diálogo, se abre en el [editor de cuadro de diálogo](../windows/dialog-editor.md).|
|**Import**|Se abre el **importar** cuadro de diálogo donde puede navegar al recurso desea importar en el proyecto actual. Puede importar un mapa de bits, icono, cursor, HTML, sonido (. WAV), o el archivo de recursos personalizados.|
|**Custom**|Se abre el **nuevo recurso personalizado** cuadro de diálogo donde puede crear un recurso personalizado. Recursos personalizados sólo se editan en el editor binario.|

Use la **nuevo recurso personalizado** cuadro de diálogo para crear un nuevo recurso personalizado en un proyecto de C++ con la siguiente propiedad:

|Property|Descripción|
|-|-|
|**Tipo de recurso**|Proporciona un cuadro de texto para escribir el nombre de un tipo de recurso personalizado. Visual C++ aprovecha automáticamente el nombre cuando se cierra el **nuevo recurso personalizado** cuadro de diálogo.|

### <a name="to-create-a-new-resource"></a>Para crear un recurso nuevo

Puede crear un nuevo recurso mediante lo siguiente:

- En **vista de recursos**, seleccione el archivo .rc y luego seleccione el **editar** menú y elija **Agregar recurso**. En el **Agregar recurso** cuadro de diálogo, seleccione el tipo de recurso que le gustaría agregar a su proyecto.

   > [!TIP]
   > También puede haga clic en el archivo .rc en **vista de recursos** y elija **Agregar recurso** en el menú contextual.

- En **el Explorador de soluciones**, haga clic en la carpeta del proyecto y seleccione **agregar**, a continuación, elija **Agregar recurso** en el menú contextual. En el **Agregar recurso** cuadro de diálogo, seleccione el tipo de recurso que le gustaría agregar a su proyecto.

   > [!NOTE]
   > Si aún no tiene un archivo .rc en el proyecto, este paso creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.

- En [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en la clase y elija **agregar**. Seleccione **Agregar recurso** en el menú contextual y elija el tipo de recurso que le gustaría agregar a su proyecto.

- En el **proyecto** menú, elija **Agregar recurso**.

## <a name="create-a-resource-template"></a>Crear una plantilla de recursos

Una plantilla de recursos es un recurso personalizado que ha guardado como un archivo .rct. Una plantilla de recursos, a continuación, actúa como punto de partida para crear recursos. Las plantillas de recursos ahorran tiempo en el desarrollo de recursos adicionales o grupos de recursos que comparten características, como los controles estándar o repiten los elementos. Por ejemplo, si desea incluir un botón de ayuda con un icono del logotipo de empresa en varios cuadros de diálogo, cree una nueva plantilla de cuadro de diálogo y personalizarlo con el botón de ayuda y el logotipo.

Después de personalizar la plantilla de recursos, guarde los cambios en la carpeta de plantillas (o la ubicación especificada en la ruta de acceso de inclusión) para que aparezca bajo su tipo de recurso en el **Agregar recurso** cuadro de diálogo. Ahora puede usar la nueva plantilla de recursos tantas veces como sea necesario.

> [!NOTE]
> El editor de recursos proporciona automáticamente un identificador de recurso único. Puede revisar el [propiedades del recurso](../windows/changing-the-properties-of-a-resource.md) según sea necesario.

> [!NOTE]
> Coloque los archivos de plantilla específicos del idioma en subdirectorios del directorio principal de plantillas. Por ejemplo, coloque los archivos de plantilla solo en inglés de... \\< directorio de plantillas de recursos\>\1033. Visual Studio busca nuevos archivos RCT en Visual Studio \Program Files\Microsoft \<versión\>\VC\VCResourceTemplates en Visual Studio \Program Files\Microsoft \<versión > \VC\VCResourceTemplates\\< LCID\> (por ejemplo, 1033 para inglés), *o* en cualquier parte de la [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md). Si prefiere guardar los archivos RCT en otra ubicación, por ejemplo, Mis documentos, deberá agregar esta carpeta a la ruta de inclusión para que Visual Studio pueda encontrar su archivo RCT.

### <a name="to-create-a-resource-template"></a>Para crear una plantilla de recursos

1. En **el Explorador de soluciones**, haga clic en el proyecto.

1. En el menú contextual, seleccione **agregar**, a continuación, elija **Agregar nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo el **plantillas:** panel, seleccione **el archivo de plantilla de recursos (.rct)**.

1. Proporcione un nombre y una ubicación para el nuevo archivo .rct y elija **abierto**.

   El nuevo archivo .rct se agregará al proyecto y aparece en **el Explorador de soluciones** bajo el **recursos** carpeta.

1. Haga doble clic en el archivo .rct para abrirlo en una ventana de documento. Para agregar recursos, haga clic en el archivo en la ventana de documento y elija **Agregar recurso**.

   Puede personalizar estos recursos y guarde el archivo .rct.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Para convertir un archivo de recursos existente en una plantilla

1. Abra el archivo .rc como un archivo independiente.

1. En el **archivo** menú, seleccione **guardar \< *filename*> como**.

1. Especifique una ubicación y elija **Aceptar**.

### <a name="to-create-a-new-resource-from-a-template"></a>Para crear un nuevo recurso a partir de una plantilla

1. En el **vista de recursos** panel, haga clic en el archivo .rc y elija **Agregar recurso** en el menú contextual.

1. En el **Agregar recurso** cuadro de diálogo, seleccione el signo más (**+**) junto a un recurso para expandir el nodo de recursos y ver todas las plantillas disponibles para ese recurso.

1. Haga doble clic en la plantilla que desea editar.

1. Modifique el recurso agregado en su editor de recursos según sea necesario.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>