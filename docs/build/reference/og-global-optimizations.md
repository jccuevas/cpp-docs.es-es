---
title: -Og (optimizaciones globales) | Documentos de Microsoft
ms.custom: ''
ms.date: 09/22/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs:
- C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 196e89a958ce49bf5e0087d98d2f40ada210cc87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="og-global-optimizations"></a>/Og (optimizaciones globales)

Desusado. Proporciona optimizaciones locales y globales, asignación automática de registros y optimización de bucles. Se recomienda que utilice [/O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [/O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en su lugar.

## <a name="syntax"></a>Sintaxis

> /Og

## <a name="remarks"></a>Comentarios

**/ Og** está en desuso. Por lo general, estas optimizaciones ahora están habilitadas de forma predeterminada. Para obtener más información acerca de las optimizaciones, consulte [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [/Ox (habilitar más velocidad optimizaciones)](../../build/reference/ox-full-optimization.md).

Las siguientes optimizaciones están disponibles en **/Og**:

- Eliminación de subexpresiones comunes locales y globales

     En esta optimización, el valor de una subexpresión común se calcula una vez. En el ejemplo siguiente, si los valores de `b` y `c` no cambia entre las tres expresiones, el compilador puede asignar el cálculo de `b + c` a una variable temporal y sustituir la variable para `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     Para la optimización de subexpresiones comunes locales, el compilador examina en secciones breves del código de subexpresiones comunes. Para la optimización de subexpresiones comunes globales, el compilador busca subexpresiones comunes en funciones completas.

- Asignación automática de registro

     Esta optimización permite al compilador a las variables de la tienda que se usan con frecuencia y subexpresiones en los registros; el `register` se omite la palabra clave.

- Optimización de bucle

     Esta optimización elimina las subexpresiones invariables desde el cuerpo de un bucle. Un bucle óptimo sólo contiene expresiones cuyos valores varían en cada ejecución del bucle. En el ejemplo siguiente, la expresión `x + y` no cambia en el cuerpo del bucle:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

     Después de la optimización, `x + y` se calcula una vez en lugar de cada vez que se ejecuta el bucle:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

     La optimización de bucles es mucho más eficaz cuando el compilador no puede suponer ningún alias, que establece con [__restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), o [restringir](../../cpp/restrict.md).

    > [!NOTE]
    > Puede habilitar o deshabilitar la optimización global en una función por función utilizando la `optimize` pragma junto con el `g` opción.

 Para obtener información relacionada, consulte [/Oi (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md) y [/Ox (habilitar más velocidad optimizaciones)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)

[Opciones del compilador](../../build/reference/compiler-options.md)

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)