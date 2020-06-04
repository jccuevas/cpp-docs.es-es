---
title: warning (pragma)
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: d8b110d459bba1e0b7e2fd6e2c95e7eed638fc99
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416188"
---
# <a name="warning-pragma"></a>warning (pragma)

Habilita la modificación selectiva del comportamiento de los mensajes de advertencia del compilador.

## <a name="syntax"></a>Sintaxis

> **advertencia #pragma (** \
> &nbsp;&nbsp;&nbsp;&nbsp;*Warning-Specifier* **:** *Warning-Number-List*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *Warning-Specifier* **:** *Warning-Number-List* ...] **)** \
> **#pragma ADVERTENCIA (Inserte** [ **,** *n* ] **)** \
> **ADVERTENCIA #pragma (pop)**

## <a name="remarks"></a>Observaciones

Los siguientes parámetros de warning-specifier están disponibles.

|warning-specifier|Significado|
|------------------------|-------------|
|*1, 2, 3, 4*|Aplica el nivel dado a las advertencias especificadas. También activa una advertencia especificada que está desactivada de forma predeterminada.|
|*valor predeterminado*|Restablece el comportamiento de advertencia a su valor predeterminado. También activa una advertencia especificada que está desactivada de forma predeterminada. La advertencia se generará en su nivel predeterminado documentado.<br /><br /> Para obtener más información, vea [advertencias del compilador desactivadas de forma predeterminada](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*disable*|No emita los mensajes de advertencia especificados.|
|*error*|Notifica las advertencias especificadas como errores.|
|*once*|Muestra los mensajes especificados solo una vez.|
|*suprimi*|Inserta el estado actual de la pragma en la pila, deshabilita la advertencia especificada para la línea siguiente y, a continuación, extrae de la pila la advertencia para que se restablezca el estado de pragma.|

En la instrucción de código siguiente se muestra que un parámetro `warning-number-list` puede contener varios números de advertencia, y que se pueden especificar varios parámetros `warning-specifier` en la misma directiva pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Esta directiva es funcionalmente equivalente al código siguiente:

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning C4385 only once.
#pragma warning( once : 4385 )

// Report warning C4164 as an error.
#pragma warning( error : 164 )
```

El compilador agrega 4000 a cualquier número de advertencia que esté entre 0 y 999.

Para los números de advertencia en el intervalo 4700-4999, que son los asociados a la generación de código, el estado de la advertencia en vigor cuando el compilador encuentra la definición de función estará en vigor para el resto de la función. El uso de la pragma **Warning** en la función para cambiar el estado de un número de advertencia mayor que 4699 solo surte efecto después del final de la función. En el ejemplo siguiente se muestra la ubicación correcta de las pragmas de **ADVERTENCIA** para deshabilitar un mensaje de advertencia de generación de código y, a continuación, restaurarlo.

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

Tenga en cuenta que a lo largo de un cuerpo de función, el último valor de pragma **Warning** estará en vigor para toda la función.

## <a name="push-and-pop"></a>Inserción y extracción

La pragma **Warning** también admite la sintaxis siguiente, donde *n* representa un nivel de advertencia (de 1 a 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

La `warning( push )` pragma almacena el estado de advertencia actual para cada advertencia. La instrucción pragma `warning( push, n )` almacena el estado actual de cada advertencia y establece el nivel de advertencia global en *n*.

Pragma `warning( pop )` extrae el último estado de advertencia insertado en la pila. Se deshacen los cambios realizados en el estado de advertencia entre la *extracción* y el *pop* . En este ejemplo:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Al final de este código, *pop* restaura el estado de cada ADVERTENCIA (incluye 4705, 4706 y 4707) a lo que estaba al principio del código.

Al escribir archivos de encabezado, puede usar la *función de extracción y de* *extracción* para garantizar que los cambios de estado de advertencia realizados por un usuario no impidan que los encabezados se compilen correctamente. Use la *extracción* al principio del encabezado y el *pop* al final. Por ejemplo, si tiene un encabezado que no se compila correctamente en el nivel de ADVERTENCIA 4, el código siguiente cambia el nivel de advertencia a 3 y, a continuación, restaura el nivel de advertencia original al final del encabezado.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Para obtener más información sobre las opciones del compilador que ayudan a suprimir advertencias, vea [/fi](../build/reference/fi-name-forced-include-file.md) y [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Consulte también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
