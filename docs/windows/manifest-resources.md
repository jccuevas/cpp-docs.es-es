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
ms.openlocfilehash: 1c9a1786e5b3a6fb150e3e27fb459ac4341486ca
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604793"
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

Para una aplicación de Windows XP o Windows Vista, el recurso de manifiesto no solo especifica que la aplicación usa la versión más reciente de los controles comunes de Windows (la 0, tal como se indica anteriormente), sino que también es compatible con el [control Syslink](http://msdn.microsoft.com/library/windows/desktop/bb760706).

Para ver la versión y escriba la información contenida en un recurso del manifiesto, puede abrir el archivo en un visor XML o en Visual Studio [Editor de texto](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Para obtener más información, vea el tema sobre cómo [abrir un recurso del manifiesto en el editor de texto de Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. . Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea  [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="limitations"></a>Limitaciones

Solo puede tener un recurso de manifiesto por módulo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)  
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)