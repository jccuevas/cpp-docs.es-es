---
title: Error de las herramientas del vinculador LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353236"
---
# <a name="linker-tools-error-lnk2005"></a>Error de las herramientas del vinculador LNK2005

> *símbolo* ya definido en el objeto

El *símbolo* de símbolo se definió más de una vez.

Este error es seguido por el error fatal [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Posibles causas y soluciones

Por lo general, este error significa que ha roto la regla de *definición,* que solo permite una definición para cualquier plantilla, función, tipo u objeto utilizado en un archivo de objeto determinado, y solo una definición en todo el ejecutable para objetos o funciones visibles externamente.

Aquí están algunas causas comunes para este error.

- Este error puede producirse cuando un archivo de encabezado define una variable. Por ejemplo, si incluye este archivo de encabezado en más de un archivo de origen en el proyecto, se produce un error:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Entre las posibles soluciones se incluyen:

  - Declare la `extern` variable en `extern int global_int;`el archivo de encabezado: , defina e inicialícela opcionalmente en un único archivo de origen: `int global_int = 17;`. Esta variable es ahora un global que puede usar `extern`en cualquier archivo de origen declarándola, por ejemplo, incluyendo el archivo de encabezado. Recomendamos esta solución para variables que deben ser globales, pero una buena práctica de ingeniería de software minimiza las variables globales.

  - Declare la [static](../../cpp/storage-classes-cpp.md#static)variable `static int static_int = 17;`static : . Esto restringe el ámbito de la definición al archivo de objeto actual y permite que varios archivos de objeto tengan su propia copia de la variable. No se recomienda definir variables estáticas en archivos de encabezado debido a la posibilidad de confusión con las variables globales. Prefiere mover definiciones de variables estáticas a los archivos de origen que las utilizan.

  - Declare la variable `__declspec(selectany) int global_int = 17;` [selectany](../../cpp/selectany.md): . Esto indica al vinculador que elija una definición para su uso por todas las referencias externas y que descarte el resto. Esta solución a veces resulta útil cuando se combinan bibliotecas de importación. De lo contrario, no se recomienda como una manera de evitar errores del vinculador.

- Este error puede producirse cuando un archivo `inline`de encabezado define una función que no es . Si incluye este archivo de encabezado en más de un archivo de origen, obtendrá varias definiciones de la función en el ejecutable.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Entre las posibles soluciones se incluyen:

  - Agregue `inline` la palabra clave a la función:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Quite el cuerpo de la función del archivo de encabezado y deje solo la declaración y, a continuación, implemente la función en un único archivo de origen:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Este error también puede producirse si define funciones miembro fuera de la declaración de clase en un archivo de encabezado:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Para corregir este problema, mueva las definiciones de la función miembro dentro de la clase. Las funciones miembro definidas dentro de una declaración de clase se insertan implícitamente.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Este error puede producirse si vincula más de una versión de la biblioteca estándar o CRT. Por ejemplo, si intenta vincular las bibliotecas CRT comerciales y de depuración, o las versiones estáticas y dinámicas de una biblioteca, o dos versiones diferentes de una biblioteca estándar al ejecutable, este error puede notificarse muchas veces. Para solucionar este problema, quite toda una copia de cada biblioteca del comando de vínculo. No se recomienda mezclar bibliotecas comerciales y de depuración, o diferentes versiones de una biblioteca, en el mismo ejecutable.

   Para indicar al vinculador que utilice bibliotecas distintas de las predeterminadas, en la línea de comandos, especifique las bibliotecas que se va a utilizar y utilice la opción [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para deshabilitar las bibliotecas predeterminadas. En el IDE, agregue referencias al proyecto para especificar las bibliotecas que se van a usar y, a continuación, abra el cuadro de diálogo **Páginas** de propiedades del proyecto y, en la página de propiedades **Vinculador**, **Entrada,** establezca las propiedades **Omitir todas las bibliotecas predeterminadas**o **Ignorar bibliotecas predeterminadas específicas** para deshabilitar las bibliotecas predeterminadas.

- Este error puede producirse si se mezcla el uso de bibliotecas estáticas y dinámicas cuando se utiliza la opción [/clr.](../../build/reference/clr-common-language-runtime-compilation.md) Por ejemplo, este error puede producirse si compila un archivo DLL para su uso en el ejecutable que vincula en el CRT estático. Para solucionar este problema, utilice solo bibliotecas estáticas o solo bibliotecas dinámicas para todo el ejecutable y para las bibliotecas que cree para usarlas en el ejecutable.

- Este error puede producirse si el símbolo es una función empaquetada (creada mediante la compilación con [/Gy](../../build/reference/gy-enable-function-level-linking.md)) y se incluyó en más de un archivo, pero se cambió entre compilaciones. Para solucionar este problema, vuelva a compilar todos los archivos que incluyan la función empaquetada.

- Este error puede producirse si el símbolo se define de forma diferente en dos objetos miembro en bibliotecas diferentes y se utilizan ambos objetos miembro. Una forma de solucionar este problema cuando las bibliotecas están vinculadas estáticamente es usar el objeto miembro de una sola biblioteca e incluir esa biblioteca primero en la línea de comandos del vinculador. Para utilizar ambos símbolos, debe crear una forma de distinguirlos. Por ejemplo, si puede crear las bibliotecas desde el origen, puede ajustar cada biblioteca en un espacio de nombres único. Como alternativa, puede crear una nueva biblioteca contenedora que utilice nombres únicos para ajustar las referencias a una de las bibliotecas originales, vincular la nueva biblioteca a la biblioteca original y, a continuación, vincular el ejecutable a la nueva biblioteca en lugar de a la biblioteca original.

- Este error puede `extern const` producirse si una variable se define dos veces y tiene un valor diferente en cada definición. Para corregir este problema, defina la constante solo `enum class` una vez o use espacios de nombres o definiciones para distinguir las constantes.

- Este error puede producirse si utiliza uuid.lib en combinación con otros archivos .lib que definen GUID (por ejemplo, oledb.lib y adsiid.lib). Por ejemplo:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Para corregir este problema, agregue [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) a las opciones de línea de comandos del vinculador y asegúrese de que uuid.lib es la primera biblioteca a la que se hace referencia.
