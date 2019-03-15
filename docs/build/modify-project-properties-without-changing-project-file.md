---
title: Filtrar Modificar las propiedades del proyecto de C++ y los destinos sin necesidad de cambiar el archivo de proyecto
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827954"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Filtrar Modificar las propiedades del proyecto de C++ y los destinos sin necesidad de cambiar el archivo de proyecto

Puede invalidar las propiedades y los destinos del proyecto desde la línea de comandos de MSBuild sin cambiar el archivo de proyecto. Esto es útil cuando se quieren aplicar algunas propiedades de manera ocasional o temporal. Se presuponen ciertos conocimientos de MSBuild. Para obtener más información, vea [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Para crear el archivo .props o .targets, puede usar el Editor XML de Visual Studio o cualquier editor de texto. No use el **Administrador de propiedades** en este escenario ya que agrega las propiedades al archivo de proyecto.

*Para reemplazar las propiedades del proyecto:*

1. Cree un archivo .props en el que se especifiquen las propiedades que se quieren invalidar.

1. Desde el símbolo del sistema: establezca ForceImportBeforeCppTargets="C:\sources\my_props.props".

*Para reemplazar los destinos del proyecto:*

1. Cree un archivo .targets con su implementación o un destino concreto.

2. Desde el símbolo del sistema: establezca ForceImportAfterCppTargets ="C:\sources\my_target.targets".

También puede establecer cualquiera de las opciones en la línea de comandos de msbuild mediante la opción /p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

El reemplazo de propiedades y destinos de esta manera equivale a agregar las importaciones siguientes a todos los archivos .vcxproj de la solución:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
