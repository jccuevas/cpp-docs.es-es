---
title: '#line (Directiva) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220228"
---
# <a name="line-directive-cc"></a>#line (Directiva) (C++C/)

La directiva **#line** indica al preprocesador que cambie el número de línea y el nombre de archivo almacenados internamente del compilador a un número de línea y un nombre de archivo determinados.

## <a name="syntax"></a>Sintaxis

> **#line** *digit-Sequence* ["*nombre de archivo*"]

## <a name="remarks"></a>Comentarios

El compilador utiliza el número de línea y el nombre de archivo opcional para hacer referencia a los errores que encuentra durante la compilación. El número de línea suele referirse a la línea de entrada actual, y el nombre de archivo hace referencia al archivo de entrada actual. El número de línea se incrementa una vez que se procesa cada línea.

El valor *de la secuencia de dígitos* puede ser cualquier constante entera. El reemplazo de macros se pueden realizar en los tokens de preprocesamiento, pero el resultado debe evaluarse como la sintaxis correcta. El *nombre de archivo* puede ser cualquier combinación de caracteres y debe incluirse entre comillas`" "`dobles (). Si se omite *filename* , el nombre de archivo anterior permanece inalterado.

Puede modificar el número de línea de código fuente y el nombre de archivo escribiendo una directiva de **#line** . El traductor utiliza el número de línea y el nombre de archivo para determinar los valores de las `__FILE__` macros predefinidas y `__LINE__`. Estas macros se pueden utilizar para insertar mensajes de error autodescriptivos en el texto del programa. Para obtener más información sobre estas macros predefinidas, vea [macros predefinidas](../preprocessor/predefined-macros.md).

La `__FILE__` macro se expande a una cadena cuyo contenido es el nombre de archivo, entre comillas dobles`" "`().

Si se cambia el número de línea y el nombre de archivo, el compilador omite los valores anteriores y continúa el procesamiento con los nuevos valores. Los generadores de programas suelen usar la directiva **#line** para hacer que los mensajes de error hagan referencia al archivo de código fuente original en lugar de al programa generado.

En los siguientes ejemplos se muestran #line `__LINE__` y `__FILE__` las macros y.

En esta instrucción, el número de línea almacenado internamente se establece en 151 y el nombre de archivo se cambia a Copy. c.

```C
#line 151 "copy.c"
```

En este ejemplo, la macro `ASSERT` usa las `__LINE__` macros predefinidas `__FILE__` e imprime un mensaje de error sobre el archivo de código fuente si una aserción determinada no es true.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
