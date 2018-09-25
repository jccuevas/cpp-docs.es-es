---
title: 'Páginas de propiedades MIDL: General | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: 0692484c-a7e6-4270-8df7-981589368399
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32e1c743844d252b391a4a747d803ba0e8c81c54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431429"
---
# <a name="midl-property-pages-general"></a>Páginas de propiedades MIDL: General

En la página de propiedades **General** de la carpeta **MIDL** se especifican las opciones del compilador MIDL siguientes:

- Definiciones del preprocesador [(/D](https://msdn.microsoft.com/library/windows/desktop/aa367321))

- Directorios de inclusión adicionales ([/I](https://msdn.microsoft.com/library/windows/desktop/aa367328))

- Omitir ruta de acceso de inclusión estándar ([/no_def_idir](https://msdn.microsoft.com/library/windows/desktop/aa367347))

- Compatible con MkTypLib ([/mktyplib203](https://msdn.microsoft.com/library/windows/desktop/aa367332))

- Nivel de advertencia ([/W](https://msdn.microsoft.com/library/windows/desktop/aa367383))

- Advertir como error ([/WX](https://msdn.microsoft.com/library/windows/desktop/aa367387))

- Suprimir la pancarta de inicio ([/nologo](https://msdn.microsoft.com/library/windows/desktop/aa367341))

- Tipo de carácter MIDL ([/char](https://msdn.microsoft.com/library/windows/desktop/aa367314))

- Entorno de destino ([/env](https://msdn.microsoft.com/library/windows/desktop/aa367323))

- Generar proxies sin código auxiliar ([/Oicf](https://msdn.microsoft.com/library/windows/desktop/aa367352))

Para obtener información sobre cómo acceder a la página de propiedades **General** de la carpeta **MIDL**, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

Para obtener información sobre cómo acceder mediante programación a las opciones de MIDL para los proyectos de C++, vea el objeto <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Vea también

[Páginas de propiedades MIDL](../ide/midl-property-pages.md)