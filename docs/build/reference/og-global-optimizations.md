---
title: /Og (optimizaciones globales)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: e8032d7dbd771ca1527c6515a779b0f532a2c658
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420874"
---
# <a name="og-global-optimizations"></a>/Og (optimizaciones globales)

Desusado. Proporciona las optimizaciones globales y locales, asignación automática de registros y la optimización de bucle. Se recomienda usar ya sea [/O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [/O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en su lugar.

## <a name="syntax"></a>Sintaxis

> /Og

## <a name="remarks"></a>Comentarios

**/ Og** está en desuso. Por lo general, estas optimizaciones ahora están habilitadas de forma predeterminada. Para obtener más información acerca de las optimizaciones, consulte [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [/Ox (habilitar más las optimizaciones de velocidad)](../../build/reference/ox-full-optimization.md).

Las siguientes optimizaciones están disponibles en **/Og**:

- Eliminación de subexpresiones comunes locales y globales

   En esta optimización, el valor de una subexpresión común se calcula una vez. En el ejemplo siguiente, si los valores de `b` y `c` no cambian entre las tres expresiones, el compilador puede asignar el cálculo de `b + c` a una variable temporal y sustituya la variable para `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Para la optimización de subexpresiones comunes locales, el compilador examina corto secciones de código de subexpresiones comunes. Para la optimización de subexpresiones comunes globales, el compilador busca funciones completas de subexpresiones comunes.

- Asignación automática de registro

   Esta optimización permite al compilador subexpresiones y variables de almacén de uso frecuente en los registros; el `register` se omite la palabra clave.

- Optimización de bucle

   Esta optimización elimina las subexpresiones invariables del cuerpo de un bucle. Un bucle óptimo sólo contiene expresiones cuyos valores se cambien a través de cada ejecución del bucle. En el ejemplo siguiente, la expresión `x + y` no cambia en el cuerpo del bucle:

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

   Optimización de bucle es mucho más eficaz cuando el compilador no puede suponer ningún alias, lo cual se establece con [__restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), o [restringir](../../cpp/restrict.md).

   > [!NOTE]
   > Puede habilitar o deshabilitar la optimización global sobre el uso de una función por función la `optimize` pragma junto con el `g` opción.

Para obtener información relacionada, consulte [/Oi (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md) y [/Ox (habilitar más las optimizaciones de velocidad)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Especifique la opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)

[Opciones del compilador](../../build/reference/compiler-options.md)

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
