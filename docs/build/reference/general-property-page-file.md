---
title: Página de propiedades General (Archivo)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 66e26cabf5af85091000e6cda144898789c581df
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826361"
---
# <a name="general-property-page-file"></a>Página de propiedades General (Archivo)

Al seleccionar un archivo en el **Explorador de soluciones**, la página de propiedades **General** bajo el nodo **Propiedades de configuración** contiene las propiedades siguientes:

- **Excluir de la compilación**

   Especifica si el archivo debe estar en la compilación para la configuración actual.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Herramienta**

   La herramienta que se va a usar para compilar este archivo. Vea [Especificar las herramientas de compilación personalizadas](../specifying-custom-build-tools.md) para obtener más información.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Para obtener información sobre cómo obtener acceso a la **General** página de propiedades bajo la **propiedades de configuración** nodo, vea [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

Para los proyectos que no sean Windows, consulte [referencia de página de propiedades de C++ Linux](../../linux/prop-pages-linux.md).

## <a name="see-also"></a>Vea también

[Referencia de página de propiedades de proyecto de C++](property-pages-visual-cpp.md)