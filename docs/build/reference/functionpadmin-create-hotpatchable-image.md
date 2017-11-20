---
title: -FUNCTIONPADMIN (crear una imagen) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /functionpadmin
dev_langs: C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f286cf0cb595f640768f97c1619517f6000fd39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)
Prepara una imagen para la aplicación de revisiones recientes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `space` (opcional)  
 La cantidad de relleno que se agregará al principio de cada función, 5, 6 o 16.  x86 imágenes requieren 5 bytes de relleno, x64 imágenes requieren 6 bytes y las imágenes creadas para la familia del procesador Itanium requieren 16 bytes de relleno al principio de cada función.  
  
 De forma predeterminada, el compilador agregará la cantidad correcta de espacio para la imagen, basándose en el tipo de equipo de la imagen.  
  
 En orden para que el vinculador generar una imagen a, los archivos .obj deben haberse compilados con [/hotpatch (crear una imagen)](../../build/reference/hotpatch-create-hotpatchable-image.md).  
  
 Cuando se compila y vincula una imagen con una sola invocación de cl.exe, **/hotpatch** implica **/functionpadmin**.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)