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
ms.openlocfilehash: b66a207766962856cc4d7181607868c2a48ebe84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513657"
---
# <a name="resource-files-c"></a>Archivos de recursos (C++)

> [!NOTE]
> . Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Use el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados.
>
> Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

El término *archivo de recursos* puede hacer referencia a varios tipos de archivo, como:

- El archivo de script de recursos (.rc) de un programa.

- Un archivo de plantilla de recursos (.rct).

- Un recurso individual existente como archivo independiente. Este tipo incluye un archivo de mapa de bits, icono o cursor al que se hace referencia desde un archivo. rc.

- Archivo de encabezado generado por el entorno de desarrollo. Este tipo incluye `Resource.h`, al que se hace referencia desde un archivo. rc.

Los recursos que se encuentran en otros tipos de archivo, como. exe,. dll y. res, se conocen como *recursos*.

Puede trabajar con *recursos* y *archivos de recursos* desde dentro del proyecto. También puede trabajar con aquellos que no forman parte del proyecto actual o que se crearon fuera del entorno de desarrollo de Visual Studio. Por ejemplo, se puede:

- Trabajar con archivos de recursos anidados e incluidos condicionalmente.

- Actualizar recursos existentes o convertirlos en objetos C++visuales.

- Importar o exportar recursos gráficos al archivo de recursos actual o desde él.

- Incluir identificadores compartidos o de solo lectura (símbolos) que no se pueden modificar por el entorno de desarrollo.

- Incluir recursos en el archivo ejecutable (. exe) que no necesiten edición (o no se deben editar), como recursos compartidos entre varios proyectos.

- Incluir tipos de recursos no admitidos en el entorno de desarrollo.

Para obtener más información sobre los recursos, vea cómo [crear recursos](../windows/how-to-create-a-resource-script-file.md), [administrar recursos](../windows/how-to-copy-resources.md)e [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Recursos de edición

Se pueden abrir los siguientes tipos de archivos para editar los recursos que contienen:

| Nombre del archivo | Descripción |
|---|---|
| .rc | Archivos de script de recursos |
| .rct | Archivos de plantilla de recursos |
| .res | Archivos de recursos |
| .resx | Archivos de recursos administrados |
| .exe | Archivos ejecutables |
| .dll | Archivos de biblioteca de vínculos dinámicos |
| . bmp,. ico,. dib,. cur | Archivos de mapa de bits, icono, barra de herramientas y cursor |

Al editar recursos, el entorno de Visual Studio funciona con y afecta a los siguientes archivos:

| Nombre del archivo | Descripción |
|---|---|
| Resource.h | Archivo de encabezado generado por el entorno de desarrollo que contiene definiciones de símbolos.<br/><br/>Incluir este archivo en el control de código fuente. |
| Filename.aps | Versión binaria del archivo de script de recursos actual usado para la carga rápida.<br /><br /> Los editores de recursos no leen directamente los archivos. RC o Resource. h. El compilador de recursos los compila en archivos. APS utilizados por los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos.<br/><br/>Al igual que con un proceso de compilación normal, la información que no es simbólica, como los comentarios, se descarta durante el proceso de compilación.<br/><br/>Siempre que el archivo. APS no esté sincronizado con el archivo. rc, se volverá a generar el archivo. rc. Por ejemplo, al **Guardar**, el editor de recursos sobrescribe el archivo. RC y el archivo resource. h. Cualquier cambio en los propios recursos permanece incorporado en el archivo. rc, pero los comentarios siempre se perderán una vez que se sobrescriba el archivo. rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Normalmente, no se debe incluir el archivo. APS en el control de código fuente. |
| .rc | Archivo de script de recursos que contiene script para los recursos del proyecto actual. Este archivo se sobrescribe con el archivo .aps cada vez que se guarda.<br/><br/>Incluir este archivo en el control de código fuente. |

## <a name="manifest-resources"></a>Recursos del manifiesto

En C++ los proyectos de escritorio, los recursos de manifiesto son archivos XML que describen las dependencias que utiliza una aplicación. Por ejemplo, en Visual Studio, este archivo de manifiesto generado por el Asistente de MFC define qué versión de los archivos dll de controles comunes de Windows debe usar la aplicación:

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

En el caso de una aplicación de Windows XP o Windows Vista, el recurso de manifiesto debe especificar la versión más reciente de los controles comunes de Windows que va a usar la aplicación. En el ejemplo anterior se `6.0.0.0`usa la versión, que es compatible con el [control Syslink](/windows/win32/Controls/syslink-overview).

> [!NOTE]
> Solo puede tener un recurso de manifiesto por módulo.

Para ver la información de versión y tipo contenida en un recurso del manifiesto, abra el archivo en un visor XML o en el editor de texto de Visual Studio. Si abre un recurso de manifiesto desde [Vista de recursos](../windows/resource-view-window.md), el recurso se abrirá en formato binario.

### <a name="to-open-a-manifest-resource"></a>Para abrir un recurso del manifiesto

1. Abra el proyecto en Visual Studio y vaya a **Explorador de soluciones**.

1. Expanda la carpeta **archivos de recursos** y, a continuación:

   - Para abrir en el editor de texto, haga doble clic en el archivo *. manifest* .

   - Para abrir en otro editor, haga clic con el botón secundario en el archivo *. manifest* y seleccione **abrir con**. Especifique el editor que se va a usar y seleccione **abrir**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
