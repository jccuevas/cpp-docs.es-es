---
title: Página de propiedades General (Archivo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
dev_langs:
- C++
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 523ac16a647116f4d18da7e516adb4f0e6bb7fc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324040"
---
# <a name="general-property-page-file"></a>Página de propiedades General (Archivo)

Al seleccionar un archivo en el **Explorador de soluciones**, la página de propiedades **General** bajo el nodo **Propiedades de configuración** contiene las propiedades siguientes:

**Excluir de la compilación**  
Especifica si el archivo debe estar en la compilación para la configuración actual.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

**Herramienta**  
La herramienta que se va a usar para compilar este archivo. Vea [Especificar las herramientas de compilación personalizadas](../ide/specifying-custom-build-tools.md) para obtener más información.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Para obtener información sobre cómo acceder a la página de propiedades **General** bajo el nodo **Propiedades de configuración**, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

Para proyectos distintos de Windows, vea [Referencia de las páginas de propiedades de un proyecto de Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../ide/property-pages-visual-cpp.md)  