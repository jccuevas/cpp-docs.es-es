---
title: Archivos de recursos (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 4d56a62dfa350b3113a28355433130563464c6be
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320541"
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)

> [!NOTE]
> . Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

El término "archivo de recursos" puede hacer referencia a varios tipos de archivo, incluidos:

- El archivo de script de recursos (.rc) de un programa.

- Un archivo de plantilla de recursos (.rct).

- Un recurso individual existente como archivo independiente, como un archivo de mapa de bits, icono o cursor al que se hace referencia a partir de un archivo .rc.

- Un archivo de encabezado generado por el entorno de desarrollo, por ejemplo, Resource.h, al que se hace referencia a partir de un archivo .rc.

También se encuentran los recursos en otros tipos de archivo como .exe, .dll y. res archivos. Puede trabajar con recursos y archivos de recursos desde dentro de su proyecto y los que no forman parte de su proyecto actual. También puede trabajar con archivos de recursos que no se crearon en el entorno de desarrollo de Visual Studio. Por ejemplo, se puede:

- Trabajar con archivos de recursos anidados e incluidos condicionalmente.

- Actualizar recursos existentes o convertirlos al formato de Visual C++.

- Importar o exportar recursos gráficos al archivo de recursos actual o desde él.

- Incluir identificadores compartidos o de solo lectura (símbolos) que no se pueden modificar por el entorno de desarrollo.

- Incluir recursos en el archivo ejecutable (.exe) que no requieran edición (o que no debería modificarse) durante el proyecto actual, como los recursos compartidos entre varios proyectos.

- Incluir tipos de recursos no admitidos en el entorno de desarrollo.

Esta sección se explica cómo:

- [Creación de recursos](../windows/how-to-create-a-resource-script-file.md)

- [Administración de recursos](../windows/how-to-copy-resources.md)

- [Incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)

## <a name="editable-resource-file-types"></a>Tipos de archivo de recursos editables

Los siguientes tipos de archivos se pueden abrir para editar los recursos que contienen:

|Nombre del archivo|Descripción|
|---------|-----------------|
|.rc|Archivos de script de recursos|
|.rct|Archivos de plantilla de recursos|
|.res|Archivos de recursos|
|.resx|Archivos de recursos administrados|
|.exe|Archivos ejecutables|
|.dll|Archivos de biblioteca de vínculos dinámicos|
|.bmp, .ico, .dib y .cur|Archivos de mapa de bits, icono, barra de herramientas y archivos de cursor.|

El entorno de Visual Studio funciona con y afecta a los siguientes archivos durante la sesión de edición de recursos:

|Nombre del archivo|Descripción|
|---------------|-----------------|
|Resource.h|Archivo de encabezado generado por el entorno de desarrollo; contiene las definiciones de símbolos. (Incluye este archivo en el control de código fuente).|
|Filename.aps|Versión binaria del archivo actual de script de recursos; se utiliza para acelerar la carga.<br /><br /> Los editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como el proceso de compilación con una normal, se descarta la información que no es simbólica (por ejemplo, los comentarios) durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md). (Normalmente, no debe incluir el archivo .aps en control de código fuente.)|
|.rc|Archivo de script de recursos que contiene script para los recursos del proyecto actual. Este archivo se sobrescribe con el archivo .aps cada vez que se guarda. (Incluye este archivo en el control de código fuente).|

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

### <a name="to-open-a-manifest-resource"></a>Para abrir un recurso del manifiesto

1. Abra el proyecto en Visual Studio.

1. Vaya a **el Explorador de soluciones** y expanda el **archivos de recursos** carpeta.

   - Editor de texto, haga doble clic en el archivo de manifiesto.

   - Para ver otros editores, haga clic en el archivo .manifest y seleccione **abrir con...** , a continuación, especifique el editor y elija **abierto**.

> [!NOTE]
> Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>