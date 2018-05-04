---
title: -Os, -Ot (favorecer código pequeño, favorecer código rápido) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
dev_langs:
- C++
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f97ab0a53eb82b65149ea0f27139743e065f7ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Favorecer código pequeño, favorecer código rápido)
Minimiza o maximiza el tamaño de los archivos exe y DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Os  
/Ot  
```  
  
## <a name="remarks"></a>Comentarios  
 **/OS** (favorecer código pequeño) minimiza el tamaño de los archivos exe y DLL, que indica al compilador que dé prioridad al tamaño sobre la velocidad. El compilador puede reducir numerosas construcciones de C y C++ a secuencias funcionalmente similares de código máquina. En ocasiones, estas diferencias ofrecen contrapartidas de tamaño frente a la velocidad. El **/Os** y **/Ot** opciones le permiten especificar la preferencia de una frente a otra:  
  
 **/Ot** (favorecer código rápido) maximiza la velocidad de los archivos exe y DLL al ordenar al compilador que dé prioridad a velocidad por encima de tamaño. (Este es el valor predeterminado). El compilador puede reducir numerosas construcciones de C y C++ a secuencias funcionalmente similares de código máquina. En ocasiones, estas diferencias ofrecen contrapartidas de tamaño frente a la velocidad. La opción /Ot está implícita en maximizar velocidad ([/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) opción. El **/O2** opción combina varias opciones para generar un código muy rápido.  
  
 Si usa **/Os** o **/Ot**, a continuación, debe especificar también [/Og](../../build/reference/og-global-optimizations.md) para optimizar el código.  
  
> [!NOTE]
>  Información que se recopila de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, [optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
 **x86 específico**  
  
 Ejemplo de código siguiente muestra la diferencia entre el favorecer código pequeño (**/Os**) Opciones y favorecer código rápido (**/Ot**) opción:  
  
> [!NOTE]
>  El siguiente describe el comportamiento esperado cuando se usa **/Os** o **/Ot**. Sin embargo, comportamiento del compilador de una versión a otra penada optimizaciones diferentes para el código siguiente.  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 Como se muestra en el fragmento de código máquina inferior, si DIFFER.c se compila para el tamaño (**/Os**), el compilador implementa la expresión de multiplicación en la instrucción return explícitamente como una multiplicación para generar una secuencia de código corta pero más lenta:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 Como alternativa, si DIFFER.c se compila para acelerar el proceso (**/Ot**), el compilador implementa la expresión de multiplicación en la instrucción return como una serie de desplazamiento y `LEA` instrucciones para generar una secuencia rápida pero más larga de código:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **END x86 específico**  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **optimización** página de propiedades.  
  
4.  Modificar el **tamaño o velocidad** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)