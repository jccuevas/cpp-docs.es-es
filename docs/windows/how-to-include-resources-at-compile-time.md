---
title: "Cómo: incluir recursos en tiempo de compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
dev_langs: C++
helpviewer_keywords:
- compiling source code, including resources
- comments [C++], compiled files
- resources [Visual Studio], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 201985a10d0f5a58fc7d617e307d2715bf29be32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-include-resources-at-compile-time"></a>Cómo: Incluir recursos en tiempo de compilación
Normalmente, es fácil y cómodo trabajar con la organización predeterminada de todos los recursos en un archivo de script de recursos (.rc). Sin embargo, puede agregar recursos de otros archivos al proyecto actual en tiempo de compilación enumerándolos en el **directivas de tiempo de compilación** cuadro el [cuadro de diálogo de inclusión de recursos](../windows/resource-includes-dialog-box.md).  
  
 Hay varias razones para incluir recursos en un archivo distinto del archivo .rc principal:  
  
-   Para agregar comentarios a instrucciones de recursos que no se eliminen al guardar el archivo .rc.  
  
     Los editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como en un proceso de compilación normal, la información que no es simbólica (por ejemplo, los comentarios) se descarta durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc.  
  
-   Para incluir recursos que ya se desarrollaron y se probaron y que no necesitan más modificaciones. (Los editores de recursos no podrán editar los archivos que se incluyan sin una extensión .rc).  
  
-   Para incluir recursos que se usan en proyectos diferentes o que forman parte de un sistema de control de versiones de código fuente y, por lo tanto, deben existir en una ubicación central donde las modificaciones afectarán a todos los proyectos.  
  
-   Para incluir recursos (por ejemplo, recursos RCDATA) que se encuentran en un formato personalizado. Los recursos RCDATA podrían tener requisitos especiales. Por ejemplo, no puede usar una expresión como valor del campo nameID. Consulte la documentación existente sobre [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] para obtener más información.  
  
 Si tiene secciones en los archivos .rc que cumplen alguna de estas condiciones, debe colocar las secciones en uno o varios archivos .rc independientes e incluyan en el proyecto con el [cuadro de diálogo de inclusión de recursos](../windows/resource-includes-dialog-box.md). El *Projectname*archivo. RC2 creado en el subdirectorio \res de un nuevo proyecto se usa para este propósito.  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>Para incluir recursos en el proyecto en tiempo de compilación  
  
1.  Sitúe los recursos en un archivo de script de recursos con un nombre de archivo único. No utilice *projectname*.rc, porque es el nombre de archivo utilizado para el archivo de script de recursos principal.  
  
2.  Haga clic en el archivo .rc (en [vista de recursos](../windows/resource-view-window.md)) y elija **incluye recursos** en el menú contextual.  
  
3.  En el **directivas de tiempo de compilación** , agregue el [#include](../preprocessor/hash-include-directive-c-cpp.md) directiva de compilador para incluir el nuevo archivo de recursos en el archivo de recursos principal en el entorno de desarrollo.  
  
     Los recursos de los archivos incluidos de esta manera pasan a formar parte del archivo ejecutable en tiempo de compilación. No están directamente disponibles para la edición o la modificación cuando se trabaja en el archivo .rc principal del proyecto. Deberá abrir por separado los archivos .rc incluidos. Los editores de recursos no podrán editar los archivos que se incluyan sin una extensión .rc.  
  

  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)