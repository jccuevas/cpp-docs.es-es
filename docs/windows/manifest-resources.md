---
title: Recursos del manifiesto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1520cd301fa46fb4d9521fd6d4180ebd3710f67
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218255"
---
# <a name="manifest-resources"></a>Recursos del manifiesto

Los recursos de manifiesto son archivos XML que describen las dependencias que utiliza una aplicación. Por ejemplo, en Visual Studio, el archivo de manifiesto generado por el asistente de MFC define cuál de los archivos DLL de controles comunes de Windows debe usar la aplicación, si la versión 5.0 o la 6.0:

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

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor XML o en Visual Studio [Editor de texto](https://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Para obtener más información, vea el tema sobre cómo [abrir un recurso del manifiesto en el editor de texto de Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](https://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="limitations"></a>Limitaciones

Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)  
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)