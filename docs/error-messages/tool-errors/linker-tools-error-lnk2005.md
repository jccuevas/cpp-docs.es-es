---
title: Las herramientas del vinculador LNK2005 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b20d3037649e99419250f1b3ec4255f2e87e31e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718827"
---
# <a name="linker-tools-error-lnk2005"></a>Error de las herramientas del vinculador LNK2005

> *símbolo* ya definido en objeto  
  
El símbolo *símbolo* se definió más de una vez.
  
Este error va seguido de un error irrecuperable [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### <a name="possible-causes-and-solutions"></a>Las posibles causas y soluciones  
  
Por lo general, este error significa que han interrumpido la *regla de una definición*, lo que permite una única definición para cualquier plantilla utilizada, la función, el tipo o el objeto en un archivo de objeto dado y solo una definición en el archivo ejecutable completo para los objetos visibles externamente o funciones.  
  
Estas son algunas causas comunes de este error.  
  
-   Este error puede producirse cuando un archivo de encabezado define una variable. Por ejemplo, si incluye este archivo de encabezado en más de un archivo de código fuente en el proyecto, se produce un error:  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    Entre las posibles soluciones están:  
  
    -   Declarar la variable `extern` en el archivo de encabezado: `extern int global_int;`, a continuación, volver a definirlo y, opcionalmente, inicializarlo en uno y solo un archivo de código fuente: `int global_int = 17;`. Esta variable es ahora una global que puede usar en cualquier archivo de origen declarándola `extern`, por ejemplo, incluyendo el archivo de encabezado. Se recomienda esta solución para las variables que deben ser globales, pero la práctica de ingeniería de software minimiza las variables globales.  
    
    -   Declarar la variable [estático](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Esto limita el ámbito de la definición para el archivo de objeto actual y permite que varios archivos de objeto tener su propia copia de la variable. No se recomienda que definir las variables estáticas en archivos de encabezado debido a la posible confusión con variables globales. Se prefieren mover las definiciones de variables estáticas a los archivos de origen que los usan.  
  
    -   Declarar la variable [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. Esto indica al vinculador para seleccionar una definición para su uso por todas las referencias externas y descartar el resto. Esta solución a veces es útil al combinar las bibliotecas de importación. En caso contrario, no se recomienda, como una manera de evitar errores del vinculador.  
  
-   Este error puede producirse cuando un archivo de encabezado define una función que no sea `inline`. Si incluye este archivo de encabezado en más de un archivo de código fuente, obtendrá varias definiciones de la función en el archivo ejecutable.  
    
    ```h  
    // LNK2005_func.h  
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Entre las posibles soluciones están:  
  
    -   Agregar el `inline` palabra clave a la función: 

        ```h  
        // LNK2005_func_inline.h  
        inline int sample_function(int k) { return 42 * (k % 167); }  
        ```  
  
    -   Quite el cuerpo de función del archivo de encabezado y deje sólo la declaración, a continuación, implemente la función en uno y solo un archivo de código fuente:  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   Este error puede producirse también si define las funciones de miembro fuera de la declaración de clase en un archivo de encabezado:  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Para corregir este problema, mueva las definiciones de función miembro dentro de la clase. Las funciones miembro definidas dentro de una declaración de clase se alinean de forma implícita.  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   Este error puede producirse si crea un vínculo más de una versión de la biblioteca estándar o CRT. Por ejemplo, si intenta vincular tanto la versión comercial y bibliotecas de depuración de CRT o las versiones estáticas y dinámicas de una biblioteca o dos versiones diferentes de una biblioteca estándar a su archivo ejecutable, este error se puede informar muchas veces. Para corregir este problema, quite todo menos una copia de cada biblioteca del comando de vínculo. No se recomienda mezclar los minoristas y depurar las bibliotecas o distintas versiones de una biblioteca, en el mismo archivo ejecutable.  
  
    Para indicar al enlazador que use bibliotecas distintas de los valores predeterminados, en la línea de comandos, especifique las bibliotecas para usar y usar el [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) opción para deshabilitar las bibliotecas predeterminadas. En el IDE, agregue referencias a su proyecto para especificar las bibliotecas para usar y, a continuación, abra el **páginas de propiedades** cuadro de diálogo para el proyecto y en el **vinculador**, **entrada** propiedad página, establezca cualquiera **omitir todas las bibliotecas predeterminadas**, o **omitir las bibliotecas específicas de predeterminado** propiedades para deshabilitar las bibliotecas predeterminadas.   
  
-   Este error puede producirse si mezcla el uso de bibliotecas estáticas y dinámicas cuando se usa el [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción. Por ejemplo, este error puede producirse si compila un archivo DLL para su uso en el archivo ejecutable que los vínculos de CRT estático. Para corregir este problema, use sólo bibliotecas estáticas o solo las bibliotecas dinámicas para todo el ejecutable y las bibliotecas que se compila para usar en el archivo ejecutable.  
  
-   Este error puede producirse si el símbolo es una función empaquetada (creada al compilar con [/Gy](../../build/reference/gy-enable-function-level-linking.md)) y se incluyó en más de un archivo, pero se ha cambiado entre las compilaciones. Para corregir este problema, vuelva a compilar todos los archivos que incluyen la función empaquetada.  
  
-   Este error puede producirse si el símbolo está definido de manera diferente en dos objetos miembro de diferentes bibliotecas y se usan dos objetos miembros. Una manera de corregir este problema cuando se vinculan estáticamente las bibliotecas es usar el objeto de miembro de sólo una biblioteca, e incluir esa biblioteca en primer lugar en la línea de comandos del vinculador. Para usar dos símbolos, debe crear una forma de distinguirlos. Por ejemplo, si puede compilar las bibliotecas de código fuente, puede encapsular cada biblioteca en un espacio de nombres único. Como alternativa, puede crear una nueva biblioteca de contenedor que usa nombres únicos para ajustar las referencias a una de las bibliotecas originales, la nueva biblioteca de vínculos a la biblioteca original y después vincular el archivo ejecutable a la nueva biblioteca en lugar de la biblioteca original.  
  
-   Este error puede producirse si un `extern const` variable se define dos veces y tiene un valor diferente en cada definición. Para corregir este problema, defina la constante solo una vez o usar espacios de nombres o `enum class` definiciones para distinguir las constantes.  
  
-   Este error puede producirse si usa uuid.lib en combinación con otros archivos .lib que definen GUID (por ejemplo, oledb.lib y adsiid.lib). Por ejemplo:  
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Para corregir este problema, agregue [/Force: Multiple](../../build/reference/force-force-file-output.md) a opciones de línea de comandos del vinculador y asegúrese de que uuid.lib es la primera biblioteca al que hace referencia.
  
## <a name="additional-information"></a>Información adicional  
  
Si usa una versión anterior del conjunto de herramientas, consulte estos artículos de Knowledge Base para obtener más información acerca de las causas concretas de este error:  
  
-   [Se produce un error de LNK2005 cuando la biblioteca CRT y las bibliotecas MFC están vinculadas en el orden incorrecto en Visual C++](https://support.microsoft.com/kb/148652)  
  
-   [CORRECCIÓN: Delete sobrecargado Global operador causas LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [Recibir errores LNK2005 cuando se compila un proyecto ejecutable (.exe) de ATL de Visual C++](https://support.microsoft.com/kb/184235).  
  
