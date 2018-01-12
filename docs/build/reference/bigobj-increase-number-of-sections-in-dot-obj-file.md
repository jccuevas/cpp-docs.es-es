---
title: "-/bigobj (aumentar el número de secciones en. Archivo de obj) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /bigobj
dev_langs: C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384ec0de9e5cb1b3172b980bf7f412abe759ff91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Aumentar el número de secciones en el archivo .Obj)
**/bigobj** aumenta el número de secciones que puede contener un archivo de objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>Comentarios  
 De manera predeterminada, un archivo objeto puede contener hasta 65.536 (2^16) secciones direccionables. Este es el caso independientemente de la plataforma de destino que se especifique. **/bigobj** incrementa esa capacidad de direccionamiento a 4.294.967.296 (2 ^ 32).  
  
 La mayoría de los módulos nunca generarán un archivo .obj que contenga más de 65.536 secciones. Sin embargo, un código generado por el equipo o un código que usa intensivamente las bibliotecas de plantillas puede requerir archivos .obj que puedan contener más secciones. **/bigobj** está habilitada de forma predeterminada en los proyectos de la tienda de Windows porque el código XAML generado por el equipo incluye un gran número de encabezados. Si deshabilita esta opción en un proyecto de aplicación de la Tienda Windows, probablemente encontrará el error del compilador C1128.  
  
 Los vinculadores distribuidos antes de Visual C++ 2005 no pueden leer archivos .obj que se hayan generado con **/bigobj**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)