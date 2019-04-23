---
title: Operador de pegado de token (##)
ms.date: 11/04/2016
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: dab4da5fd65fc280d2061256a580a015917d24b6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029948"
---
# <a name="token-pasting-operator-"></a>Operador de pegado de token (##)

El operador de signo de número doble o "pegado de token" (**##**), que a veces se denomina operador de "combinación", se usa en las macros de tipo de objeto y de tipo función. Permite que se unan tokens distintos en un solo token y, por tanto, no puede ser el primero ni el último token en la definición de macro.

Si un parámetro formal en una definición de macro va precedido o seguido del operador de pegado de token, el parámetro formal se sustituye inmediatamente por el argumento real sin expandir. La expansión de la macro no se realiza en el argumento antes de la sustitución.

A continuación, cada repetición del operador de pegado de token en *token-string* se quita, y los tokens anteriores y posteriores se concatenan. El token resultante debe ser un token válido. Si es válido, el token se analiza para una posible sustitución en caso de que represente un nombre de macro. El identificador representa el nombre por el que se conocerán los tokens concatenados en el programa antes de la sustitución. Cada token representa un token definido en alguna parte, ya sea dentro del programa o en la línea de comandos del compilador. El espacio en blanco que precede o que sigue al operador es opcional.

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