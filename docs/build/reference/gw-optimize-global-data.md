---
title: -Gw (optimizar datos globales) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Gw
dev_langs:
- C++
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e849ee51a231c6f0d3d696a3aaa9b1c1ac77c33c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="gw-optimize-global-data"></a>/Gw (optimizar datos globales)
Empaquete los datos globales en las secciones COMDAT para la optimización.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Gw[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **/Gw** opción hace que el compilador empaquete los datos globales en las secciones COMDAT. De forma predeterminada, **/Gw** está desactivada y debe habilitarse explícitamente. Para deshabilitarlo explícitamente, utilice **/Gw-**. Cuando ambos **/Gw** y [/GL](../../build/reference/gl-whole-program-optimization.md) está habilitada, el vinculador utiliza la optimización de todo el programa para comparar las secciones COMDAT entre varios archivos objeto con el fin de excluir los datos globales o para combinar sólo lectura globales datos idénticos. Esto puede reducir significativamente el tamaño del archivo ejecutable binario resultante.  
  
 Cuando se compila y vincula por separado, puede usar el [/OPT: ref](../../build/reference/opt-optimizations.md) opción del vinculador que se excluirán el ejecutable los datos globales sin referencia en archivos objeto compilados con la **/Gw** opción.  
  
 También puede usar el [/OPT: ICF](../../build/reference/opt-optimizations.md) y [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opciones del vinculador juntas para combinar en el archivo ejecutable que los de solo lectura globales datos idénticos entre varios archivos objeto compilados con la **/Gw** opción.  
  
 Para obtener más información, consulte [Introducción /Gw modificador del compilador](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) en el Blog del equipo de Visual C++.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir **/Gw** y, a continuación, elija **Aceptar**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)