---
title: "-IMPLIB (nombre de biblioteca de importación) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 523fc171aa8df3d0b4c6e09909db7c2c1dc0b833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implib-name-import-library"></a>/IMPLIB (Asignar nombre a la biblioteca de importación)
  
> /IMPLIB:*nombre de archivo*  
  
## <a name="parameters"></a>Parámetros  
  
*filename*  
Un nombre especificado por el usuario para la biblioteca de importación. Reemplaza el nombre predeterminado.  
  
## <a name="remarks"></a>Comentarios  
  
La opción/IMPLIB invalida el nombre predeterminado de la biblioteca de importación que LINK crea cuando compila un programa que contiene exportaciones. El nombre predeterminado se forma a partir del nombre base del archivo de salida principal y la extensión. lib. Un programa contiene exportaciones si se especifican uno o varios de los siguientes:  
  
-   El [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) palabra clave en el código fuente  
  
-   [EXPORTACIONES](../../build/reference/exports.md) instrucción en un archivo .def  
  
-   Un [/exportación](../../build/reference/export-exports-a-function.md) especificación en un comando de LINK  
  
 LINK omite/IMPLIB cuando no se está creando una biblioteca de importación. Si no se especifica ninguna exportación, LINK no creará una biblioteca de importación. Si se usa un archivo de exportación en la compilación, vínculo se supone que ya existe una biblioteca de importación y no crea uno. Para obtener información sobre las bibliotecas de importación y exportación de archivos, consulte [referencia de LIB](../../build/reference/lib-reference.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **avanzadas** página de propiedades.  
  
4.  Modificar el **biblioteca de importación** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)