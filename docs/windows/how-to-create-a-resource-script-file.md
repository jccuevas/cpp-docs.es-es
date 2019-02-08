---
title: Filtrar Crear un archivo de Script de recursos (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
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
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 9055e0f787c238276d3134c2fa6a8afae0102433
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905685"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Filtrar Crear un archivo de Script de recursos (C++)

> [!NOTE]
> El **Editor de recursos** no está disponible en las ediciones Express.
>
> Este material se aplica a aplicaciones de escritorio de Windows. Los proyectos en lenguajes .NET no utilizan archivos de script de recursos. Para obtener más información, consulte [archivos de recursos](../windows/resource-files-visual-studio.md).

## <a name="to-create-a-new-resource-script-rc-file"></a>Para crear un nuevo archivo de script de recursos (.rc)

1. Coloca el foco en la carpeta del proyecto existente en **el Explorador de soluciones**, por ejemplo, `MyProject`.

   > [!NOTE]
   > No confunda la carpeta del proyecto con la carpeta de soluciones en **el Explorador de soluciones**. Si coloca el foco en el **solución** carpeta, sus elecciones en el **Agregar nuevo elemento** cuadro de diálogo (en el paso 3) serán diferente.

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione el **Visual C++** a continuación, elija la carpeta **archivo de recursos (.rc)** en el panel derecho.

1. Proporcione un nombre para el archivo de script de recursos en el **nombre** texto cuadro y luego elija **abierto**.

A partir de ese momento, podrá [crear](../windows/how-to-create-a-resource.md) y agregar recursos al archivo .rc.

> [!NOTE]
> Solo se puede agregar un script de recursos (archivo .rc) a un proyecto existente que esté cargado en el IDE de Visual Studio. No es posible crear archivos .rc independientes (fuera de un proyecto). [Las plantillas de recursos](../windows/how-to-use-resource-templates.md) (archivos .rct) pueden crearse en cualquier momento.

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>Para abrir un archivo de script de recursos fuera de un proyecto de C++ (independiente)

Puede ver los recursos en un archivo .rc sin tener un proyecto abierto. El archivo .rc se abrirá en una ventana de documento en lugar de abrirse en el [vista de recursos](../windows/resource-view-window.md) ventana (como ocurre cuando el archivo se abre dentro de un proyecto).

> [!NOTE]
> Esta distinción es importante porque algunos comandos solo están disponibles cuando el archivo se abre de forma independiente (fuera de un proyecto). Por ejemplo, puede guardar solo un archivo en un formato diferente o como un nombre de archivo diferente cuando se abre el archivo fuera de un proyecto (el **Guardar como** comando no está disponible cuando se abre un archivo dentro de un proyecto).

### <a name="to-open-an-rc-file-outside-a-project"></a>Para abrir un archivo .rc fuera de un proyecto

1. Desde el **archivo** menú, elija **abierto**, a continuación, seleccione **archivo**.

1. En el **abrir archivo** diálogo cuadro, vaya al archivo de script de recursos que desea ver, resalte el archivo y seleccione **abierto**.

   > [!NOTE]
   > Si abre primero el proyecto (**archivo**, **abrir**, **proyecto**), algunos comandos no estarán disponibles para usted. Abrir un archivo "independiente" significa abrir sin cargar primero el proyecto.

### <a name="to-open-multiple-rc-files-outside-a-project"></a>Para abrir varios archivos .rc fuera de un proyecto

1. Abra ambos archivos de recursos de manera independiente. Por ejemplo, abra `Source1.rc` y `Source2.rc`.

   1. Desde el **archivo** menú, elija **abierto**, a continuación, seleccione **archivo**.

   1. En el **abrir archivo** cuadro de diálogo, navegue hasta el primer archivo de script de recursos que desee abrir (`Source1.rc`), resalte el archivo y elija **abrir**.

   1. Repita el paso anterior para abrir el segundo archivo .rc (`Source2.rc`).

       Los archivos .rc ahora están abiertos en ventanas de documentos independientes.

1. Cuando los archivos .rc estén abiertos, coloque las ventanas en mosaico para poder verlos simultáneamente:

   - Desde el **ventana** menú, elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical**.

       \- o -

   - Haga clic en uno de los archivos .rc y elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical** en el menú contextual.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-open-a-resource-script-file-in-text-format"></a>Para abrir un archivo de script de recursos en formato de texto

Puede haber ocasiones en que desee ver el contenido del archivo de script de recursos (.rc) del proyecto sin abrir un recurso, como un cuadro de diálogo, en su editor de recursos específico. Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos que contiene y realizar operaciones globales admitidas por el editor de texto.

> [!NOTE]
> Los editores de recursos no leen directamente .rc o `resource.h` archivos. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como en un proceso de compilación normal, la información que no es simbólica (por ejemplo, los comentarios) se descarta durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>Para abrir un archivo de script de recursos como texto

1. Desde el **archivo** menú elija **abierto**, a continuación, elija **archivo**.

1. En el **abrir archivo** cuadro de diálogo, navegue hasta el archivo de script de recursos que desea ver en formato de texto.

1. Resalte el archivo y luego seleccione la flecha desplegable en el **abierto** (situado a la derecha del botón).

1. Elija **abrir con** en el menú desplegable.

1. En el **abrir con** cuadro de diálogo, seleccione **Editor de código fuente (texto)**.

1. Desde el **abrir como** lista desplegable, seleccione **texto**.

   El recurso se abrirá en el **código fuente** editor.

\- o -

1. En **el Explorador de soluciones**, haga clic en el archivo .rc.

1. En el menú contextual, elija **abrir con...** , a continuación, seleccione **Editor de código fuente (texto)**.

## <a name="to-add-mfc-support-to-resource-script-files"></a>Para agregar compatibilidad con MFC a archivos de script de recursos

Normalmente, cuando crea una aplicación MFC para Windows usando el [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos (como un archivo de recursos (.rc) de la secuencia de comandos) que contiene las características principales de Microsoft Foundation clases (MFC). Sin embargo, si edita un archivo .rc para una aplicación de Windows que no se basa en MFC, las siguientes características específicas para el marco de trabajo MFC no están disponibles:

- Asistentes para código MFC

- Cadenas de mensajes de menú

- Contenidos de listas de controles de cuadro combinado

- Hospedaje de controles ActiveX

Sin embargo, puede agregar compatibilidad con MFC a archivos .rc que no lo tienen.

> [!NOTE]
> Estos pasos requieren MFC.

### <a name="to-add-mfc-support-to-rc-files"></a>Para agregar compatibilidad con MFC a archivos .rc

1. Abra el archivo de script de recursos.

1. En [vista de recursos](../windows/resource-view-window.md), resalte la carpeta de recursos (por ejemplo, MFC.rc).

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), establezca el **MFC Mode** propiedad **True**.

   > [!NOTE]
   > Además de tener que establecer este marcador, el archivo .rc deberá formar parte de un proyecto MFC. Por ejemplo, simplemente establecer **MFC Mode** a **True** en un archivo .rc en Win32 proyecto no obtendrá ninguna de las características MFC.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)