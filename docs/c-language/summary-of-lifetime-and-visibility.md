---
title: Resumen de duración y visibilidad
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: f364c3c0b558c00e3d411ab5b697ed01ec395cbd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299083"
---
# <a name="summary-of-lifetime-and-visibility"></a>Resumen de duración y visibilidad

En la tabla siguiente se muestra un resumen de características de duración y de visibilidad para la mayoría de los identificadores. Las tres primeras columnas proporcionan los atributos que definen duración y visibilidad. Un identificador con los atributos especificados por las tres primeras columnas tiene la duración y la visibilidad que se muestran en la cuarta y quinta columnas. Sin embargo, la tabla no cubre todos los casos posibles. Consulte [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener más información.

### <a name="summary-of-lifetime-and-visibility"></a>Resumen de duración y visibilidad

|Atributos:<br /><br /> Level|Elemento|Clase de almacenamiento<br /><br /> Especificador|Resultado:<br /><br /> Período de duración|Visibility|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Ámbito de archivo|Definición de variable|**static**|Global|Resto del archivo de código fuente en el que aparece|
||Declaración de variables|**extern**|Global|Resto del archivo de código fuente en el que aparece|
||Prototipo o definición de función|**static**|Global|Archivo de código fuente único|
||Prototipo de función|**extern**|Global|Resto del archivo de código fuente|
|Ámbito de bloque|Declaración de variables|**extern**|Global|Bloquear|
||Definición de variable|**static**|Global|Bloquear|
||Definición de variable|**auto** o **register**|Local|Bloquear|

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se ilustran los bloques, el anidamiento y la visibilidad de las variables:

### <a name="code"></a>Código

```c
// Lifetime_and_Visibility.c

#include <stdio.h>

int i = 1;  // i defined at external level

int main()  // main function defined at external level
{
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)
    {                                 // Begin first nested block
        int i = 2, j = 3;          // i and j defined at internal level
        printf_s( "%d %d\n", i, j );  // Prints 2, 3
        {                             // Begin second nested block
            int i = 0;                // i is redefined
            printf_s( "%d %d\n", i, j ); // Prints 0, 3
        }                             // End of second nested block
        printf_s( "%d\n", i );        // Prints 2 (outer definition
                                      //  restored)
    }                                 // End of first nested block
    printf_s( "%d\n", i );            // Prints 1 (external level
                                      // definition restored)
    return 0;
}
```

### <a name="comments"></a>Comentarios

En este ejemplo, hay cuatro niveles de visibilidad: el nivel externo y tres niveles bloqueados. Los valores se imprimen en pantalla según se indica en los comentarios que siguen a cada instrucción.

## <a name="see-also"></a>Vea también

[Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md)
