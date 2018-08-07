---
title: Archivos de recursos (Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc9a9f35793b010f4cea227ed629543c82b2ce87
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605287"
---
# <a name="resource-files-visual-studio"></a>Archivos de recursos (Visual Studio)
> [!NOTE]
>  Este material se aplica a aplicaciones de escritorio de Windows. Para obtener información sobre los recursos de aplicaciones de la plataforma Universal de Windows, consulte [definir recursos de la aplicación](http://msdn.microsoft.com/476ea844-632c-4467-9ce3-966be1350dd4).  
>   
> Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
>  
> . Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 El término "archivo de recursos" puede hacer referencia a varios tipos de archivo, incluidos:  
  
-   El archivo de script de recursos (.rc) de un programa.  
  
-   Un archivo de plantilla de recursos (.rct).  
  
-   Un recurso individual existente como archivo independiente, como un archivo de mapa de bits, icono o cursor al que se hace referencia a partir de un archivo .rc.  
  
-   Un archivo de encabezado generado por el entorno de desarrollo, por ejemplo, Resource.h, al que se hace referencia a partir de un archivo .rc.  
  
 Los recursos también se pueden encontrar en [otros tipos de archivo](../windows/editable-file-types-for-resources.md) como archivos .exe, .dll y. res. Puede trabajar con recursos y archivos de recursos dentro del proyecto y con los que no forman parte de su proyecto actual. También puede trabajar con archivos de recursos que no se crearon en el entorno de desarrollo de Visual Studio. Por ejemplo, se puede:  
  
-   Trabajar con archivos de recursos anidados e incluidos condicionalmente.  
  
-   Actualizar recursos existentes o convertirlos al formato de Visual C++.  
  
-   Importar o exportar recursos gráficos al archivo de recursos actual o desde él.  
  
-   Incluir identificadores compartidos o de solo lectura (símbolos) que no se pueden modificar por el entorno de desarrollo.  
  
-   Incluir recursos en el archivo ejecutable (.exe) que no requieran edición (o que no quiera que se editen) durante el proyecto actual, como los recursos que se comparten entre varios proyectos.  
  
-   Incluir tipos de recursos no admitidos en el entorno de desarrollo.  
  
 En esta sección se tratan los siguientes temas:  
  
-   [Creación de un archivo nuevo de script de recursos](../windows/how-to-create-a-resource-script-file.md)  
  
-   [Creación de un recurso nuevo](../windows/how-to-create-a-resource.md)  
  
-   [Visualización de recursos en un archivo de script de recursos](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [Apertura de un archivo de script de recursos en formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [Inclusión de recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [Copia de recursos](../windows/how-to-copy-resources.md)  
  
-   [Uso de plantilla de recursos (.rct)](../windows/how-to-use-resource-templates.md)  
  
-   [Importación y exportación de recursos](../windows/how-to-import-and-export-resources.md)  
  
-   [Tipos de archivos editables para recursos](../windows/editable-file-types-for-resources.md)  
  
-   [Archivos afectados al editar recursos](../windows/files-affected-by-resource-editing.md)  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)   
 [Trabajar con archivos de recursos](../windows/working-with-resource-files.md)   
 [Menús y otros recursos](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)