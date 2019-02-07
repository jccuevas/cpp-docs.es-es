---
title: Recursos de manifiesto (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850195"
---
# <a name="manifest-resources-c"></a>Recursos de manifiesto (C++)

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

Para una aplicación de Windows XP o Windows Vista, el recurso de manifiesto no solo especifica que la aplicación usa la versión más reciente de los controles comunes de Windows (la 0, tal como se indica anteriormente), sino que también es compatible con el [control Syslink](/windows/desktop/Controls/syslink-overview).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor de XML o en el editor de texto de Visual Studio. Si abre un recurso de manifiesto desde [Vista de recursos](../windows/resource-view-window.md), el recurso se abrirá en formato binario. Para ver el contenido de un recurso del manifiesto en un formato más inteligible, debe abrir el recurso de **el Explorador de soluciones**.

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>Para abrir un recurso del manifiesto en el Editor de texto

1. Con el proyecto abierto en **el Explorador de soluciones**, expanda el **archivos de recursos** carpeta.

1. Haga doble clic en el archivo .manifest.

   El recurso del manifiesto se abre en el **Editor de texto**.

## <a name="to-open-a-manifest-resource-in-another-editor"></a>Para abrir un recurso del manifiesto en otro editor

1. En **el Explorador de soluciones**, haga clic en el archivo .manifest y elija **abrir con...**  en el menú contextual.

1. En el **abrir con** cuadro de diálogo, especifique el editor que le gustaría usar y seleccione **abierto**.

## <a name="limitations"></a>Limitaciones

Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)