---
title: -Zm (especificar el límite de asignación de memoria de encabezado precompilado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zm
dev_langs:
- C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 379d3d6673e673522334d685a47220bcfa2523ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Especificar el límite de asignación de memoria del encabezado precompilado)
Determina la cantidad de memoria que el compilador asigna para construir encabezados precompilados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zmfactor  
```  
  
## <a name="arguments"></a>Argumentos  
 `factor`  
 Factor de escala que determina la cantidad de memoria que el compilador utiliza para construir encabezados precompilados.  
  
 El argumento `factor` es un porcentaje del tamaño predeterminado de un búfer de trabajo definido por el compilador. El valor predeterminado del argumento `factor` es 100 (en tanto por ciento), pero puede especificar cantidades mayores o menores.  
  
## <a name="remarks"></a>Comentarios  
 En versiones anteriores de Visual C++, el compilador utilizaba varios montones discretos, cada uno con un límite finito. Actualmente, el compilador aumenta dinámicamente los montones según sea necesario hasta un límite de tamaño de montón total, y solo requiere un búfer de tamaño fijo para construir los encabezados precompilados. Por lo tanto, la **/Zm** opción del compilador casi nunca es necesaria.  
  
 Si el compilador se queda sin espacio en el montón y emite el [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) recibe un mensaje de error cuando se usa el **/Zm** opción del compilador, que podría tiene reservado demasiada memoria. Considere la posibilidad de quitar el **/Zm** opción. Si el compilador emite la [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) mensaje de error, un [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) mensaje especifica el `factor` argumento que se utilizará al volver a compilar mediante el uso de la **/Zm** opción del compilador.  
  
 En la tabla siguiente se muestra cómo el argumento `factor` afecta al límite de asignación de memoria suponiendo que el tamaño del búfer del encabezado precompilado predeterminado es de 75 MB.  
  
|Valor de `factor`|Límite de asignación de memoria|  
|-----------------------|-----------------------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Otras maneras de establecer el límite de la asignación de memoria  
  
#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer la opción /Zm del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de navegación, seleccione **propiedades de configuración**, **C/C++**, **línea de comandos**.  
  
3.  Escriba el **/Zm** opción del compilador en el **opciones adicionales** cuadro.  
  
#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Para establecer la opción /Zm del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)