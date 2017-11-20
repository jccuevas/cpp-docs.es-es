---
title: "-GR (habilitar la información de tipo en tiempo de ejecución) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs: C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3420af666ac4b9dca648b780ae99e794265515bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Habilitar la información de tipo en tiempo de ejecución)
Agrega código para comprobar los tipos de objetos en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GR[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando **/GR** está activado, el compilador define la `_CPPRTTI` macro de preprocesador. De forma predeterminada, **/GR** se encuentra en. **/GR-** deshabilita la información de tipo en tiempo de ejecución.  
  
 Use **/GR** si el compilador no puede resolver estáticamente un tipo de objeto en el código. Suele ser preciso el **/GR** cuando el código usa [dynamic_cast (operador)](../../cpp/dynamic-cast-operator.md) o [typeid](../../cpp/typeid-operator.md). Sin embargo, **/GR** aumenta el tamaño de las secciones .rdata de la imagen. Si el código no utiliza **dynamic_cast** o **typeid**, **/GR-** puede producir una imagen más pequeña.  
  
 Para obtener más información acerca de la comprobación de tipos en tiempo de ejecución, consulte [información de tipo de tiempo de ejecución](../../cpp/run-time-type-information.md) en el *referencia del lenguaje C++*.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **lenguaje** página de propiedades.  
  
4.  Modificar el **habilitar información de tipo de tiempo de ejecución** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)