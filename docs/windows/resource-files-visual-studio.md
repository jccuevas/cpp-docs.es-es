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
ms.openlocfilehash: bd73db481659573d51e4abd56da9689e2e8ade25
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676440"
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)

> [!NOTE]
> . Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Use la [editor de imágenes](../windows/image-editor-for-icons.md) y [editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados.
>
> Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

El término *archivo de recursos* puede hacer referencia a un número de tipos de archivo, como:

- El archivo de script de recursos (.rc) de un programa.

- Un archivo de plantilla de recursos (.rct).

- Un recurso individual existente como un archivo independiente. Este tipo incluye un archivo de mapa de bits, icono o cursor que se hace referencia a un archivo .rc.

- Un archivo de encabezado generado por el entorno de desarrollo. Este tipo incluye `Resource.h`, que se hace referencia a un archivo .rc.

Encontrar recursos en otros tipos de archivo, como archivos .exe, .dll y. res se conocen como *recursos*.

Puede trabajar con *archivos de recursos* y *recursos* desde dentro del proyecto. También puede trabajar con los que no forman parte del proyecto actual o se crearon fuera del entorno de desarrollo de Visual Studio. Por ejemplo, se puede:

- Trabajar con archivos de recursos anidados e incluidos condicionalmente.

- Actualizar recursos existentes o convertirlos a Visual C++.

- Importar o exportar recursos gráficos al archivo de recursos actual o desde él.

- Incluir identificadores compartidos o de solo lectura (símbolos) que no se pueden modificar por el entorno de desarrollo.

- Incluir recursos en el archivo ejecutable (.exe) que no es necesario editar (o no debe editarse), como los recursos compartidos entre varios proyectos.

- Incluir tipos de recursos no admitidos en el entorno de desarrollo.

Para obtener más información sobre los recursos, consulte cómo [crear recursos](../windows/how-to-create-a-resource-script-file.md), [administrar recursos](../windows/how-to-copy-resources.md), y [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Recursos editables

Los siguientes tipos de archivos se pueden abrir para editar los recursos que contienen:

| Nombre del archivo | Descripción |
|---|---|
| .rc | Archivos de script de recursos |
| .rct | Archivos de plantilla de recursos |
| .res | Archivos de recursos |
| .resx | Archivos de recursos administrados |
| .exe | Archivos ejecutables |
| .dll | Archivos de biblioteca de vínculos dinámicos |
| .bmp, .ico, .dib y .cur | Archivos de mapa de bits, icono, barra de herramientas y cursor |

Al editar recursos, el entorno de Visual Studio funciona con y afecta a los siguientes archivos:

| Nombre del archivo | Descripción |
|---|---|
| Resource.h | Archivo de encabezado generado por el entorno de desarrollo que contiene las definiciones de símbolos.<br/><br/>Incluir este archivo en el control de código fuente. |
| Filename.aps | Versión binaria del archivo de script recurso actual usa para la carga rápida.<br /><br /> Editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps consumidos por los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos.<br/><br/>Como el proceso de compilación con una normal, se descarta la información que no es simbólica, tales como comentarios, durante el proceso de compilación.<br/><br/>Siempre que el archivo .aps se desincroniza con el archivo .rc, se vuelve a generar el archivo .rc. Por ejemplo, cuando se **guardar**, el editor de recursos sobrescribe el archivo .rc y resource.h. Los cambios realizados en los propios recursos permanecen incorporados en el archivo .rc, pero los comentarios siempre se perderán cuando se sobrescribe el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Por lo general, no debe incluir el archivo .aps en control de código fuente. |
| .rc | Archivo de script de recursos que contiene script para los recursos del proyecto actual. Este archivo se sobrescribe con el archivo .aps cada vez que se guarda.<br/><br/>Incluir este archivo en el control de código fuente. |

## <a name="manifest-resources"></a>Recursos del manifiesto

En proyectos de escritorio de C++, recursos de manifiesto son archivos XML que describen las dependencias de que una aplicación utiliza. Por ejemplo, en Visual Studio este MFC archivo de manifiesto generados por el asistente define qué versión de la DLL del control común de Windows debe usar la aplicación:

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

Para una aplicación de Windows XP o Windows Vista, el recurso del manifiesto debe especificar la versión más reciente de los controles comunes de Windows para que use la aplicación. El ejemplo anterior utiliza la versión `6.0.0.0`, que admite el [control Syslink](/windows/desktop/Controls/syslink-overview).

> [!NOTE]
> Solo puede tener un recurso de manifiesto por módulo.

Para ver la versión y escriba la información contenida en un recurso del manifiesto, abra el archivo en un visor de XML o editor de texto de Visual Studio. Si abre un recurso de manifiesto desde [Vista de recursos](../windows/resource-view-window.md), el recurso se abrirá en formato binario.

### <a name="to-open-a-manifest-resource"></a>Para abrir un recurso del manifiesto

1. Abra el proyecto en Visual Studio y navegue hasta **el Explorador de soluciones**.

1. Expanda el **archivos de recursos** carpeta, a continuación:

   - Para abrir el editor de texto, haga doble clic en el archivo de manifiesto.

   - Para abrir en otro editor, haga clic en el archivo .manifest y seleccione **abrir con...** . Especifique el editor y elija **abierto**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
