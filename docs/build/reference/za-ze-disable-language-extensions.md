---
title: -Za, - Ze (deshabilitar extensiones de lenguaje) | Documentos de Microsoft
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
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378150"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Deshabilitar extensiones de lenguaje)
El **/Za** opción del compilador emite un error para las construcciones de lenguaje que no son compatibles con ANSI C89 o ISO C ++ 11. El **/Ze** opción del compilador, que está activado de forma predeterminada, habilita las extensiones de Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El **/Ze** opción está en desuso porque su comportamiento está de forma predeterminada. Le recomendamos que use la [/Zc (ajuste)](../../build/reference/zc-conformance.md) opciones del compilador para controlar las características de extensión de idioma específico. Para obtener una lista de opciones del compilador en desuso, consulte el **en desuso y quitar opciones de compilador** sección [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
 El [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] compilador ofrece una serie de características más allá de los especificados en los estándares ANSI C89, ISO C99 o ISO C++. Estas características se conocen colectivamente como extensiones de Microsoft para C y C++. Estas extensiones están disponibles de forma predeterminada y no está disponible cuando la **/Za** se especifica la opción. Para obtener más información acerca de extensiones específicas, consulte [Extensions Microsoft para C y C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Se recomienda deshabilitar extensiones de lenguaje mediante la especificación de la **/Za** opción si piensa migrar el programa a otros entornos. Cuando **/Za** se especifica, el compilador trata las palabras clave como identificadores simples de extendidas de Microsoft, deshabilita las demás extensiones de Microsoft y define automáticamente el `__STDC__` macro predefinida para programas de C.  
  
 Otras opciones del compilador utilizadas con **/Za** pueden afectar a cómo el compilador garantiza el cumplimiento de los estándares. Por ejemplo, **/Za** y [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md) pueden dar en el comportamiento de la promoción de tipo de punto flotante que no se ajusta a ISO C99 o C ++ 11 estándares.  
  
 Para que ver las formas especificar la configuración de comportamiento de estándares específicos, consulte la [/Zc](../../build/reference/zc-conformance.md) opción del compilador.  
  
 Para obtener más información acerca de los problemas de conformidad con [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)], consulte [comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de navegación, elija **propiedades de configuración**, **C/C++**, **lenguaje**.  
  
3.  Modificar el **deshabilitar extensiones de lenguaje** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Zc (Ajuste)](../../build/reference/zc-conformance.md)