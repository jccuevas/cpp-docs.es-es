---
title: Operador de pegado de token (##)
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 4bf1b8c8f56ab9375503c9e8fb6a906706fc70bb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218103"
---
# <a name="token-pasting-operator-"></a>Operador de pegado de token (##)

El operador de signo de número doble o de *pegado de token* ( **##** ), que a veces se denomina operador de *combinación* o *combinación* , se utiliza en macros de tipo objeto y de función. Permite unir tokens independientes en un único token y, por tanto, no puede ser el primer o el último token de la definición de macro.

Si un parámetro formal en una definición de macro va precedido o seguido del operador de pegado de token, el parámetro formal se sustituye inmediatamente por el argumento real sin expandir. La expansión de la macro no se realiza en el argumento antes de la sustitución.

A continuación, se quita cada aparición del operador de pegado de tokens en la *cadena de token* y se concatenan los tokens anteriores y posteriores. El token resultante debe ser un token válido. Si es válido, el token se analiza para una posible sustitución en caso de que represente un nombre de macro. El identificador representa el nombre por el que se conocerán los tokens concatenados en el programa antes de la sustitución. Cada token representa un token definido en alguna parte, ya sea dentro del programa o en la línea de comandos del compilador. El espacio en blanco que precede o que sigue al operador es opcional.

En este ejemplo se muestra el uso de los operadores de generación de cadenas y de pegado de token al especificar la salida del programa:

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

Si se llama a una macro con un argumento numérico como

```cpp
paster( 9 );
```

la macro produce

```cpp
printf_s( "token" "9" " = %d", token9 );
```

que se convierte en

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>Ejemplo

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>Vea también

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)
