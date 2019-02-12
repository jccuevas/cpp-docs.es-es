---
title: Archivos de recursos (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 65500644b70841f372edcc6911edefc6c7b9f432
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152695"
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)

> [!NOTE]
> Este material se aplica a aplicaciones de escritorio de Windows. Para obtener información sobre los recursos de aplicaciones de la plataforma Universal de Windows, consulte [definir recursos de la aplicación](/windows/uwp/app-resources/).
>
> Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).
>
> . Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

El término "archivo de recursos" puede hacer referencia a varios tipos de archivo, incluidos:

- El archivo de script de recursos (.rc) de un programa.

- Un archivo de plantilla de recursos (.rct).

- Un recurso individual existente como archivo independiente, como un archivo de mapa de bits, icono o cursor al que se hace referencia a partir de un archivo .rc.

- Un archivo de encabezado generado por el entorno de desarrollo, por ejemplo, Resource.h, al que se hace referencia a partir de un archivo .rc.

También se encuentran en los recursos [otros tipos de archivo](../windows/editable-file-types-for-resources.md) como archivos .exe, .dll y. res. Puede trabajar con recursos y archivos de recursos desde dentro de su proyecto y los que no forman parte de su proyecto actual. También puede trabajar con archivos de recursos que no se crearon en el entorno de desarrollo de Visual Studio. Por ejemplo, se puede:

- Trabajar con archivos de recursos anidados e incluidos condicionalmente.

- Actualizar recursos existentes o convertirlos al formato de Visual C++.

- Importar o exportar recursos gráficos al archivo de recursos actual o desde él.

- Incluir identificadores compartidos o de solo lectura (símbolos) que no se pueden modificar por el entorno de desarrollo.

- Incluir recursos en el archivo ejecutable (.exe) que no requieran edición (o que no debería modificarse) durante el proyecto actual, como los recursos compartidos entre varios proyectos.

- Incluir tipos de recursos no admitidos en el entorno de desarrollo.

Puede abrir los siguientes tipos de archivos y editar los recursos que contienen:

|Nombre del archivo|Descripción|
|---------------|-----------------|
|.rc|Archivos de scripts de recursos.|
|.rct|Archivos de plantilla de recursos.|
|.res|Archivos de recursos.|
|.resx|Archivos de recursos administrados.|
|.exe|Archivos ejecutables.|
|.dll|Archivos de la biblioteca de vínculos dinámicos.|
|.bmp, .ico, .dib y .cur|Archivos de mapa de bits, icono, barra de herramientas y archivos de cursor.|

El entorno de Visual Studio funciona con y afecta a los archivos que se muestra en la siguiente tabla durante la sesión de edición de recursos:

|Nombre del archivo|Descripción|
|---------------|-----------------|
|Resource.h|Archivo de encabezado generado por el entorno de desarrollo; contiene las definiciones de símbolos. (Incluye este archivo en el control de código fuente).|
|Filename.aps|Versión binaria del archivo actual de script de recursos; se utiliza para acelerar la carga.<br /><br /> Los editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como el proceso de compilación con una normal, se descarta la información que no es simbólica (por ejemplo, los comentarios) durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md). (Normalmente, no debe incluir el archivo .aps en control de código fuente.)|
|.rc|Archivo de script de recursos que contiene script para los recursos del proyecto actual. Este archivo se sobrescribe con el archivo .aps cada vez que se guarda. (Incluye este archivo en el control de código fuente).|

Esta sección se explica cómo:

- [Creación de recursos](../windows/how-to-create-a-resource-script-file.md)

- [Administración de recursos](../windows/how-to-copy-resources.md)

- [Incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)

## <a name="manifest-resources"></a>Recursos del manifiesto

En proyectos de escritorio de C++, recursos de manifiesto son archivos XML que describen las dependencias que utiliza una aplicación. Por ejemplo, en Visual Studio, el archivo de manifiesto generado por el asistente de MFC define cuál de los archivos DLL de controles comunes de Windows debe usar la aplicación, si la versión 5.0 o la 6.0:

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Para una aplicación de Windows XP o Windows Vista, el recurso del manifiesto no solo especifica que la aplicación utilice la versión más reciente de los controles comunes de Windows, versión 6.0, tal como se muestra anteriormente, pero también admite la [control Syslink](/windows/desktop/Controls/syslink-overview).

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor de XML o en el editor de texto de Visual Studio. Si abre un recurso de manifiesto desde [Vista de recursos](../windows/resource-view-window.md), el recurso se abrirá en formato binario. Para ver el contenido de un recurso del manifiesto en un formato más inteligible, debe abrir el recurso de **el Explorador de soluciones**.

Para abrir un recurso del manifiesto, elija los pasos siguientes:

- Editor de texto, con el proyecto abierto en **el Explorador de soluciones**, expanda el **archivos de recursos** carpeta y haga doble clic en el archivo de manifiesto.

- Para otro editor, en **el Explorador de soluciones**, haga clic en el archivo .manifest y elija **abrir con...**  en el menú contextual. En el **abrir con** cuadro de diálogo, especifique el editor que le gustaría usar y seleccione **abierto**.

> [!NOTE]
> Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Menús y otros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Controles](../mfc/controls-mfc.md)<br/>