---
title: -Gs (controlar llamadas de comprobación de la pila) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /GS
dev_langs:
- C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5665187548b1f8ace41bed281684f1a830c0ad4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375745"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (Controlar llamadas de comprobación de la pila)
Controla las comprobaciones de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>Argumentos  
 `size`  
 (Opcional) Número de bytes que pueden ocupar las variables locales antes de que se inicie un sondeo de pila. Si el **/GS** opción se especifica sin un `size` argumento, es lo mismo que especificar **/Gs0**,  
  
## <a name="remarks"></a>Comentarios  
 Un sondeo de pila es una secuencia de código que el compilador inserta en cada llamada de función. Cuando se inicia un sondeo de pila, se introduce en la memoria sin causar conflictos, en la cantidad de espacio necesaria para almacenar las variables locales de la función.  
  
 Si una función requiere más de `size` bytes de espacio de la pila para las variables locales, se activará su sondeo de pila. De forma predeterminada, el compilador genera código que inicia un sondeo de pila cuando una función requiere más de una página de espacio de pila. Esto es equivalente a una opción del compilador de **/Gs4096** para x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]y las plataformas ARM. Este valor permite a una aplicación y al administrador de memoria de Windows aumentar la cantidad de memoria asignada dinámicamente a la pila del programa en tiempo de ejecución.  
  
> [!NOTE]
>  El valor predeterminado de **/Gs4096** permite que la pila del programa de aplicaciones para Windows aumente correctamente en tiempo de ejecución. Le recomendamos que no cambie el valor predeterminado, excepto si sabe exactamente por qué tiene que cambiarlo.  
  
 Algunos programas, como los controladores de dispositivos virtuales, no requieren este mecanismo predeterminado de aumento de la pila. En esos casos, no es necesario usar sondeos de pila: puede impedir que el compilador los genere configurando `size` con un valor mayor que el que requerirán las funciones para el almacenamiento de variables locales. No se permite ningún espacio entre **/GS** y `size`.  
  
 **/ Gs0** activa las comprobaciones de pila para cada llamada de función que requiere almacenamiento para las variables locales. Esto puede afectar negativamente al rendimiento.  
  
 Puede activar o desactivar las comprobaciones de la pila mediante [check_stack](../../preprocessor/check-stack.md). **/GS** y `check_stack` pragma no tienen ningún efecto sobre las rutinas de biblioteca de C estándar; afectan a sólo las funciones que se compilan.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)