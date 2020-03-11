---
title: 'Cómo: crear recursos (C++)'
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
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866126"
---
# <a name="how-to-create-resources-c"></a>Cómo: crear recursos (C++)

Puede crear recursos para el proyecto:

- Uso de un archivo de script de recursos.

   > [!NOTE]
   > Este paso es necesario antes de agregar recursos.

- Agregar recursos al proyecto y usar el **vista de recursos**.

- Usar una plantilla de recursos para crear recursos personalizados.

## <a name="use-resource-script-files"></a>Usar archivos de script de recursos

Antes de crear y agregar nuevos recursos al proyecto, primero debe crear un archivo de script de recursos (. RC).

> [!NOTE]
> Solo puede Agregar un archivo de script de recursos a un proyecto existente cargado en el IDE de Visual Studio. No se puede crear un script de recursos independiente fuera del proyecto, aunque los archivos de plantilla de recursos (. RCT) se pueden crear en cualquier momento.

### <a name="to-create-a-resource-script-file"></a>Para crear un archivo de script de recursos

1. Coloque el foco en la carpeta del proyecto existente en **Explorador de soluciones**, por ejemplo, *suproyecto*.

   > [!NOTE]
   > No confunda la carpeta del proyecto con la carpeta de la solución en **Explorador de soluciones**. Si coloca el foco en la carpeta de la **solución** , no tendrá las mismas opciones **Agregar nuevo elemento** .

1. En el menú, vaya a **proyecto** > **Agregar nuevo elemento**.

1. Seleccione la **carpeta C++ visual** y elija **archivo de recursos (. RC)** en el panel derecho.

1. Proporcione un nombre para el archivo de script de recursos en el cuadro de texto **nombre** y seleccione **abrir**.

### <a name="to-open-a-resource-script-file"></a>Para abrir un archivo de script de recursos

Puede ver los recursos en un archivo de script de recursos sin tener un proyecto abierto. El archivo de script se abre en una ventana de documento en lugar de en el **vista de recursos**.

> [!NOTE]
> Algunos comandos solo están disponibles si el archivo se abre de forma independiente, es decir, fuera de un proyecto sin cargar primero el proyecto. Por ejemplo, para usar el comando **Guardar como** y guardar un archivo con un formato o nombre de archivo diferente, el archivo debe estar abierto de forma independiente.

- Para abrir un archivo de script de recursos fuera de un proyecto, en el menú, vaya a **archivo** > **abrir**y elija **archivo**. Navegue hasta el archivo de script de recursos, resalte el archivo y elija **abrir**.

    > [!NOTE]
    > Puede haber ocasiones en las que desee ver el contenido del archivo de script de recursos del proyecto sin usar los editores de recursos para abrir un recurso. Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente. Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos que contiene y completar las operaciones globales admitidas por el editor de texto.
    >
    > Para abrir un archivo de script de recursos en formato de texto, use la flecha desplegable situada a la derecha del botón **abrir** en el paso anterior y elija **abrir con**. Seleccione **Editor de código fuente (texto)** y, en la lista desplegable **Abrir como** , seleccione **texto** y el recurso se abrirá en el editor de **código fuente** .

- Para abrir varios scripts de recursos, siga el mismo paso anterior para cada archivo que desee abrir, por ejemplo, *Source1. RC* y *source2. RC*. A continuación, cuando ambos archivos. RC estén abiertos en ventanas de documentos independientes, use el menú **ventana** o haga clic con el botón derecho en uno de los archivos y elija **nuevo grupo de pestañas horizontal** o **nuevo grupo de pestañas vertical**. Las ventanas están ahora en mosaico para que pueda verlas simultáneamente.

> [!TIP]
> Puede abrir los archivos de script de recursos haciendo clic con el botón secundario en el archivo. RC en **Explorador de soluciones**, seleccionando **abrir con** y eligiendo **Editor de código fuente (texto)** .

Al compilar una aplicación de Microsoft Foundation Class (MFC) para Windows mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos que incluye un archivo de script de recursos (. RC) que contiene las características básicas de MFC. Sin embargo, estas características específicas de MFC no están disponibles cuando se edita un archivo. RC para aplicaciones Windows no basadas en MFC. Esto incluye asistentes para código, cadenas de mensajes de menú, contenido de la lista de controles de cuadro combinado y hospedaje de controles ActiveX.

- Para agregar compatibilidad con MFC, con el archivo de script de recursos abierto, en **vista de recursos**, resalte la carpeta recursos (por ejemplo, *MFC. RC*). A continuación, en el [ventana Propiedades](/visualstudio/ide/reference/properties-window), establezca el **modo MFC** en **true**.

  > [!NOTE]
  > Además de establecer el **modo MFC**, el archivo. RC debe formar parte de un proyecto MFC. Establecer solo el **modo de MFC** en **true** en un archivo. rc de un proyecto de Win32 no proporcionará características de MFC.

## <a name="create-resources"></a>Crear recursos

Puede crear un recurso como un nuevo recurso predeterminado, lo que significa que se trata de un recurso que no está basado en una plantilla o como un recurso con patrón después de una plantilla.

Use la ventana **vista de recursos** para mostrar los archivos de recursos incluidos en los proyectos. Al expandir la carpeta superior, por ejemplo, *Project1. RC*, se muestran los tipos de recursos de ese archivo. Expanda cada tipo de recurso para mostrar los recursos individuales de ese tipo.

> [!TIP]
> Para abrir la ventana de **vista de recursos** , vaya a la **vista** de menú > **otras ventanas** > **vista de recursos** o presione **Ctrl**+**MAYÚS**+**E**.

También puede hacer clic con el botón derecho en la ventana de **vista de recursos** para iniciar un menú contextual de comandos o hacer doble clic en la barra de título para acoplar y desacoplar la ventana. Haga clic con el botón secundario en la barra de título para los comandos que controlan el comportamiento de la ventana. Para obtener más información, consulte [Administración de Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

La **vista de recursos** Windows incluye el cuadro de diálogo **Agregar recurso** con las siguientes propiedades para agregar recursos a C++ un proyecto de aplicación de escritorio de Windows:

| Propiedad | Descripción |
|---|---|
| **Tipo de recurso** | Especifique el tipo de recurso que desea crear.<br/><br/>Puede expandir las categorías de recursos de cursor y de cuadro de diálogo para mostrar recursos adicionales, que se encuentran en *. \Microsoft Visual Studio \<versión\>\VC\VCResourceTemplates\\< LCID\>\mfc.RCT*. Si necesita agregar archivos. RCT, colóquelos aquí o especifique otra [ruta de acceso de inclusión](../windows/how-to-specify-include-directories-for-resources.md). Los recursos que se muestran en el nivel superior del control de árbol son los recursos predeterminados proporcionados por Visual Studio. Los recursos de los archivos. RCT aparecen en el segundo nivel en la categoría adecuada. No hay ningún límite preestablecido para el número de archivos. RCT que se pueden agregar.<br/><br/> |
| **Nuevo** | Cree un recurso basado en el tipo seleccionado en el cuadro **tipo de recurso** y abra el recurso en el editor adecuado.<br/><br/>Por ejemplo, si crea un recurso de cuadro de diálogo, abre el recurso en el [Editor de cuadros de diálogo](../windows/dialog-editor.md). |
| **Importar** | Abra el cuadro de diálogo **importar** para ir al recurso que desea importar en el proyecto actual.<br/><br/>Puede importar un mapa de bits, un icono, un cursor, un código HTML y un sonido (. WAV) o un archivo de recursos personalizado. |
| **Personalizada** | Abra el cuadro de diálogo **nuevo recurso personalizado** para crear un recurso personalizado.<br/><br/>También incluye una propiedad de **tipo de recurso** que proporciona un cuadro de texto para que escriba el nombre del tipo de recurso personalizado. Visual C++ pone el nombre automáticamente al salir. Los recursos personalizados solo se editan en el [Editor binario](../windows/binary-editor.md). |

Cuando se crea un nuevo recurso, visual C++ le asigna un nombre único, por ejemplo, `IDD_Dialog1`. Puede personalizar este identificador de recurso editando las propiedades del recurso en el editor de recursos asociado o en el [ventana Propiedades](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> No especifique un nombre de recurso o un identificador que esté reservado por Visual Studio. Los nombres reservados son `DESIGNINFO`, `HWB`y `TEXTINCLUDE`, y el identificador reservado es `255`.

### <a name="to-create-a-resource"></a>Para crear un recurso

- En **vista de recursos**, seleccione el archivo. RC y, a continuación, use **Editar** > **Agregar recurso** y elija el tipo de recurso que se va a agregar al proyecto.

   > [!TIP]
   > También puede hacer clic con el botón secundario en el archivo. RC en **vista de recursos** y elegir **Agregar recurso** en el menú contextual.

- En **Explorador de soluciones**, haga clic con el botón derecho en la carpeta del proyecto, seleccione **Agregar** > **Agregar recurso** y elija el tipo de recurso que se va a agregar al proyecto.

   > [!NOTE]
   > Si aún no tiene un archivo. RC en el proyecto, en este paso se creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.

- En [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón secundario en la clase, seleccione **Agregar** > **Agregar recurso** y elija el tipo de recurso que se va a agregar al proyecto.

- Use el **proyecto** de menú > **Agregar recurso**.

## <a name="use-resource-templates"></a>Uso de plantillas de recursos

Una plantilla de recursos es un recurso personalizado que ha guardado como un archivo. RCT. Una plantilla de recursos actúa como punto de partida para crear recursos. Las plantillas de recursos ahorran tiempo en el desarrollo de recursos adicionales o grupos de recursos que comparten características, como los controles estándar o los elementos repetidos. Por ejemplo, si desea incluir un botón ayuda con el icono del logotipo de la compañía en varios cuadros de diálogo, cree una nueva plantilla de cuadro de diálogo y personalícela con el botón ayuda y el logotipo.

Después de personalizar una plantilla de recursos, guarde los cambios en la carpeta de plantillas o en la ubicación especificada en la ruta de acceso de inclusión, de modo que la nueva plantilla de recursos aparezca bajo su tipo de recurso en el cuadro de diálogo **Agregar recurso** . Ahora puede usar la nueva plantilla de recursos tantas veces como sea necesario.

> [!NOTE]
> El editor de recursos proporciona automáticamente un identificador de recurso único. Puede revisar las propiedades del [recurso](../windows/changing-the-properties-of-a-resource.md) según sea necesario.

> [!NOTE]
> Coloque los archivos de plantilla específicos del idioma en los subdirectorios del directorio principal de la plantilla. Por ejemplo, los archivos de plantilla solo en inglés van en *..\\< directorio de plantillas de recursos\>\ 1033*.
>
> Visual Studio busca nuevos archivos. RCT en la carpeta *\Archivos de Programa\microsoft visual studio \<versión\>\VC\VCResourceTemplates*, *\Archivos de programa\microsoft visual studio \<versión > \VC\VCRESOURCETEMPLATES\\< LCID\>* (por ejemplo, un LCID de 1033 para inglés) o cualquier lugar de la [ruta de acceso de inclusión](../windows/how-to-specify-include-directories-for-resources.md). Si prefiere almacenar los archivos. RCT en otra ubicación, debe agregar la ubicación a la ruta de acceso de inclusión.

### <a name="to-create-and-use-a-resource-template"></a>Para crear y usar una plantilla de recursos

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Agregar nuevo elemento**.

1. En el panel **plantillas:** , seleccione **archivo de plantilla de recursos (. RCT)** .

1. Proporcione un nombre y una ubicación para el nuevo archivo *. RCT* y elija **abrir**.

   El nuevo archivo *. RCT* se agrega al proyecto y aparece en **Explorador de soluciones** en la carpeta **recursos** .

1. Haga doble clic en el archivo *. RCT* para abrirlo en una ventana de documento. Para agregar recursos, haga clic con el botón derecho en el archivo en la ventana de documento y elija **Agregar recurso**.

   Puede personalizar los recursos agregados y guardar el archivo *. RCT* .

1. En el panel **vista de recursos** , haga clic con el botón secundario en el archivo *. RC* y elija **Agregar recurso**.

1. Seleccione el signo más ( **+** ) junto a un recurso para expandir el nodo de recursos y ver las plantillas disponibles para ese recurso.

1. Haga doble clic en la plantilla que desea editar.

   Puede modificar el recurso agregado según sea necesario en su editor de recursos.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Para convertir un archivo de recursos existente en una plantilla

Con el archivo de script de recursos abierto, en el menú, vaya a **archivo** > **Guardar \<*nombre*de archivo > como**. Especifique una ubicación y elija **Aceptar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: administrar recursos](../windows/how-to-copy-resources.md)<br/>
[Procedimiento para incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)<br/>