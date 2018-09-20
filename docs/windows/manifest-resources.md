---
title: Manifiestos de recursos (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2da93d1baaf95799c7ef68d6cc854d554fbe6c47
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429570"
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

Para una aplicación de Windows XP o Windows Vista, el recurso del manifiesto no solo especifica que la aplicación usa la versión más reciente de los controles comunes de Windows (versión 6.0, tal como se muestra anteriormente), pero también admite la [control Syslink](/windows/desktop/Controls/syslink-overview).

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor de XML o en el editor de texto de Visual Studio. Para obtener más información, vea el tema sobre cómo [abrir un recurso del manifiesto en el editor de texto de Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="limitations"></a>Limitaciones

Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)