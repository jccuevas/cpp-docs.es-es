---
title: -PERFIL (generador de perfiles de herramientas de rendimiento) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15379914b4c4852e3065d1abc03c2ce1b17fb044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Generador de perfiles de Herramientas de rendimiento)
Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/PROFILE  
```  
  
## <a name="remarks"></a>Comentarios  
 /Profile implica las siguientes opciones del vinculador:  
  
-   [/ OPT: REF](../../build/reference/opt-optimizations.md)  
  
-   / OPT: NOICF  
  
-   [/ INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [/ FIJO: NO](../../build/reference/fixed-fixed-base-address.md)  
  
 / PERFIL hace que el vinculador generar una sección de reubicación en la imagen del programa.  Una sección de reubicación permite al generador de perfiles transformar la imagen del programa para obtener datos de perfil.  
  
 **/ PERFIL** solo está disponible solo en las versiones Enterprise (desarrollo en equipo).  Para obtener más información sobre PREfast, vea [análisis de código para información general de C o C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **avanzadas** página de propiedades.  
  
5.  Modificar el **perfil** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)