---
title: '#línea (directiva) (C/C ++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: e478d287af097081910d192e2ac0fbee6890bfa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614765"
---
# <a name="line-directive-cc"></a>#line (Directiva) (C/C++)

El **#line** directiva indica al preprocesador que cambie el número de línea almacenado internamente del compilador y nombre de archivo a un número de línea especificado y el nombre de archivo.

## <a name="syntax"></a>Sintaxis

> **#line** *secuencia de dígitos* ["*filename*"]

## <a name="remarks"></a>Comentarios

El compilador utiliza el número de línea y el nombre de archivo opcional para hacer referencia a los errores que encuentra durante la compilación. El número de línea suele referirse a la línea de entrada actual, y el nombre de archivo hace referencia al archivo de entrada actual. El número de línea se incrementa una vez que se procesa cada línea.

El *secuencia de dígitos* valor puede ser cualquier constante entera. El reemplazo de macros se pueden realizar en los tokens de preprocesamiento, pero el resultado debe evaluarse como la sintaxis correcta. El *filename* puede ser cualquier combinación de caracteres y debe ir entre comillas dobles (**""**). Si *filename* es se omite, el nombre de archivo anterior permanece sin cambios.

Puede modificar el número de línea de origen y el nombre de archivo escribiendo un **#line** directiva. El traductor usa el número de línea y el nombre de archivo para determinar los valores de las macros predefinidas `__FILE__` y `__LINE__`. Estas macros se pueden utilizar para insertar mensajes de error autodescriptivos en el texto del programa. Para obtener más información sobre estas macros predefinidas, vea [Macros predefinidas](../preprocessor/predefined-macros.md).

El `__FILE__` macro se expande en una cadena cuyo contenido es el nombre de archivo entrecomillado comillas dobles (**""**).

Si se cambia el número de línea y el nombre de archivo, el compilador omite los valores anteriores y continúa el procesamiento con los nuevos valores. El **#line** directiva se utiliza normalmente generadores de programas para hacer que los mensajes de error hacer referencia al archivo de origen original en lugar de al programa generado.

Los ejemplos siguientes ilustran **#line** y `__LINE__` y `__FILE__` macros.

En esta declaración, el número de línea almacenado internamente se establece en 151 y el nombre de archivo se cambia a copy.c.

```cpp
#line 151 "copy.c"
```

En este ejemplo, la macro `ASSERT` utiliza las macros predefinidas `__LINE__` y `__FILE__` para imprimir un mensaje de error sobre el archivo de código fuente si una aserción especificada no es true.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)