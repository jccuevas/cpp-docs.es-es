---
title: Macros (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: ba2c0f012974a528876219d00c61c0f31a6cd820
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218861"
---
# <a name="macros-cc"></a>Macros (C/C++)

El preprocesador expande las macros en todas las líneas excepto las *directivas*de preprocesador, las líneas que **#** tienen como primer carácter que no sea un espacio en blanco. Expande macros en partes de algunas directivas que no se omiten como parte de una compilación condicional. Las *directivas de compilación condicional* permiten suprimir la compilación de partes de un archivo de código fuente. Prueban una expresión o un identificador constante para determinar qué bloques de texto se van a pasar al compilador y cuáles se quitan del archivo de código fuente durante el preprocesamiento.

La directiva `#define` se utiliza normalmente para asociar identificadores significativos con constantes, palabras clave e instrucciones o expresiones usadas con frecuencia. Los identificadores que representan constantes a veces se denominan constantes simbólicas o *constantes de manifiesto*. Los identificadores que representan instrucciones o expresiones sedenominan macros. En esta documentación de preprocesador, solo se utiliza el término "macro".

Cuando se reconoce el nombre de una macro en el texto de origen del programa o en los argumentos de otros comandos de preprocesador, se trata como una llamada a esa macro. El nombre de la macro se reemplaza por una copia del cuerpo de la macro. Si la macro acepta argumentos, los argumentos reales que siguen al nombre de la macro se sustituyen por los parámetros formales en el cuerpo de la macro. El proceso de reemplazar una llamada de macro con la copia procesada del cuerpo se denomina *expansión* de la llamada de macro.

En la práctica, hay dos tipos de macros. Las macros *de tipo objeto* no toman ningún argumento. Las macros *de tipo función* se pueden definir para aceptar argumentos, de modo que tengan el aspecto y actúen como llamadas a funciones. Dado que las macros no generan llamadas de función reales, a veces puede hacer que los programas se ejecuten más rápido reemplazando las llamadas de función con macros. (En C++, las funciones insertadas suelen ser un método preferido). Sin embargo, las macros pueden crear problemas si no los define y los usa con cuidado. Puede que tenga que utilizar paréntesis en definiciones de macro con argumentos para conservar la prioridad correcta en una expresión. Además, puede que las macros no controlen correctamente las expresiones con efectos secundarios. Para obtener más información, vea `getrandom` el ejemplo de [la Directiva #define](../preprocessor/hash-define-directive-c-cpp.md).

Una vez definida una macro, no se puede volver a definir en un valor diferente sin quitar primero la definición original. Sin embargo, puede volver a definir la macro con exactamente la misma definición. Por lo tanto, la misma definición puede aparecer más de una vez en un programa.

La `#undef` Directiva quita la definición de una macro. Una vez que haya quitado la definición, puede volver a definir la macro con un valor diferente. [La Directiva #define](../preprocessor/hash-define-directive-c-cpp.md) y [la Directiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) describen las `#define` directivas `#undef` y, respectivamente.

Para obtener más información, vea

- [Macros y C++](../preprocessor/macros-and-cpp.md)

- [Macros variádicas](../preprocessor/variadic-macros.md)

- [Macros predefinidas](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>Vea también

[Referencia deC++ C/preprocesador](../preprocessor/c-cpp-preprocessor-reference.md)
