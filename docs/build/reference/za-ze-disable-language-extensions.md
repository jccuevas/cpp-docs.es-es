---
title: -Za, - Ze (deshabilitar extensiones de lenguaje) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e30fb37be6738b7100b84a1898c02ab4230c41b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597578"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Deshabilitar extensiones de lenguaje)
El **/Za** opción del compilador emite un error para las construcciones de lenguaje que no son compatibles con ANSI C89 o ISO C ++ 11. El **/Ze** habilita la opción del compilador, que está activada de forma predeterminada, las extensiones de Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El **/Ze** opción es obsoleta porque su comportamiento está activada de forma predeterminada. Se recomienda usar la [/Zc (ajuste)](../../build/reference/zc-conformance.md) opciones del compilador para controlar las características de extensión de lenguaje específico. Para obtener una lista de opciones del compilador en desuso, vea el **en desuso y opciones del compilador quitó** sección [Compiler Options Listed por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
 El compilador de Visual C++ ofrece una serie de características más allá de aquellas especificadas en las normas ANSI C89, ISO C99 o ISO C++. Estas características se conocen colectivamente como extensiones de Microsoft para C y C++. Estas extensiones están disponibles de forma predeterminada y no está disponible cuando el **/Za** se especifica la opción. Para obtener más información acerca de las extensiones específicas, consulte [Extensions Microsoft C y C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Se recomienda que deshabilite las extensiones de lenguaje especificando el **/Za** opción si planea trasladar un programa a otros entornos. Cuando **/Za** se especifica, el compilador trata las palabras clave como identificadores simples de extendidas de Microsoft, deshabilita las demás extensiones de Microsoft y define automáticamente el `__STDC__` la macro predefinida para los programas de C.  
  
 Puede usar con otras opciones del compilador **/Za** pueden afectar a cómo el compilador garantiza el cumplimiento de estándares. Por ejemplo, **/Za** y [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md) puede provocar un comportamiento de promoción de tipo de punto flotante que no se ajusta a ISO C99 o estándares C ++ 11.  
  
 Para que ver formas de especificar la configuración de comportamiento conforme a los estándares específicos, consulte el [/Zc](../../build/reference/zc-conformance.md) opción del compilador.  
  
 Para obtener más información acerca de problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de navegación, elija **propiedades de configuración**, **C o C++**, **lenguaje**.  
  
3.  Modificar el **deshabilitar extensiones de lenguaje** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Zc (Ajuste)](../../build/reference/zc-conformance.md)