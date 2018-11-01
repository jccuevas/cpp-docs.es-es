---
title: Recursos de manifiesto (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 081fd12a86c31973c7856ca7b9f3fcb129e2eb81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578287"
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

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor de XML o en el editor de texto de Visual Studio. Para obtener más información, vea el tema sobre cómo [abrir un recurso del manifiesto en el editor de texto de Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="limitations"></a>Limitaciones

Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)