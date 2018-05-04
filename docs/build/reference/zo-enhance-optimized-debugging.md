---
title: -Zo (mejorar la depuración optimizada) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 013738ab05bf67d3db066d94d32d398a0555c55e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (Mejorar la depuración optimizada)
Genera información de depuración mejorada para código optimizado en versiones no depuradas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
/Zo[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **/zo** modificador del compilador genera información de depuración mejorada para código optimizado. La optimización puede usar registros para variables locales, reordenar código, vectorizar bucles y llamadas a funciones en línea. Estas optimizaciones pueden interferir con la relación entre el código fuente y el código de objeto compilado. El **/zo** conmutador indica al compilador que genere información de depuración adicional para variables locales y las funciones insertadas. Usar para ver las variables en el **automático**, **locales**, y **inspección** windows cuando se recorra el código optimización en el depurador de Visual Studio. También permite que los seguimientos de pila muestren las funciones inline en el depurador WinDBG. Compilaciones de depuración que deshabilitaron las optimizaciones ([/Od](../../build/reference/od-disable-debug.md)) no necesita la información de depuración adicional generada cuando **/zo** se especifica. Use la **/zo** cambiar a configuraciones de versión de depuración con la optimización activada. Para obtener más información sobre los modificadores de optimización, vea [opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md). El **/Zo** opción está habilitada de forma predeterminada en Visual Studio cuando se especifica la información de depuración con **/Zi** o **/Z7**. Especifique **/Zo-** deshabilitar explícitamente esta opción del compilador.  
  
 El **/Zo** conmutador está disponible a partir de Visual Studio 2013 Update 3 y reemplaza el no documentado anteriormente **/d2Zi+** cambiar.  
  
### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Zo en Visual Studio  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **propiedades de configuración**, **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir `/Zo` y, a continuación, elija **Aceptar**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)   
 [/ Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [Editar y continuar](/visualstudio/debugger/edit-and-continue)