---
title: warning
ms.date: 11/04/2016
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: 1341472af22582635207a2bdff93b4367fd59330
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037755"
---
# <a name="warning-pragma"></a>warning (pragma)
Habilita la modificación selectiva del comportamiento de los mensajes de advertencia del compilador.

## <a name="syntax"></a>Sintaxis

```
#pragma warning(
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )
#pragma warning( push[ ,n ] )
#pragma warning( pop )
```

## <a name="remarks"></a>Comentarios

Los siguientes parámetros de warning-specifier están disponibles.

|warning-specifier|Significado|
|------------------------|-------------|
|*1, 2, 3, 4*|Aplica el nivel dado a las advertencias especificadas. También activa una advertencia especificada que está desactivada de forma predeterminada.|
|*default*|Restablece el comportamiento de advertencia a su valor predeterminado. También activa una advertencia especificada que está desactivada de forma predeterminada. La advertencia se generará en su nivel predeterminado documentado.<br /><br /> Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*disable*|No emite los mensajes de advertencia especificados.|
|*error*|Notifica las advertencias especificadas como errores.|
|*once*|Muestra los mensajes especificados solo una vez.|
|*suppress*|Inserta el estado actual de la pragma en la pila, deshabilita la advertencia especificada para la línea siguiente y, a continuación, extrae de la pila la advertencia para que se restablezca el estado de pragma.|

En la instrucción de código siguiente se muestra que un parámetro `warning-number-list` puede contener varios números de advertencia, y que se pueden especificar varios parámetros `warning-specifier` en la misma directiva pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Este es el equivalente funcional del código siguiente.

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

El compilador agrega 4000 a cualquier número de advertencia que esté entre 0 y 999.

Para los números de advertencia en el intervalo 4700 - 4999, que son los asociados a la generación de código, el estado de la advertencia en vigor cuando el compilador encuentra la llave de apertura de una función estará en vigor para el resto de la función. Mediante el **advertencia** pragma en la función para cambiar el estado de una advertencia que tiene un número superior a 4699 solo tendrá efecto después del final de la función. El ejemplo siguiente muestra la posición correcta de **advertencia** directivas pragma para deshabilitar un mensaje de advertencia de generación de código y, a continuación, restaurarla.

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

Tenga en cuenta que a lo largo de una función de cuerpo, el último valor de la **advertencia** pragma entrará en vigor para la función completa.

## <a name="push-and-pop"></a>Inserción y extracción

El **advertencia** pragma también admite la sintaxis siguiente, donde *n* representa un nivel de advertencia (de 1 a 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

La directiva pragma `warning( push )` almacena el estado de advertencia actual para cada advertencia. La directiva pragma `warning( push, n )` almacena el estado actual para cada advertencia y establece el nivel de advertencia global en *n*.

La directiva pragma `warning( pop )` POP el último estado de advertencia insertado en la pila. Los cambios realizados en el estado de advertencia entre *inserción* y *pop* se deshacen. Considere este ejemplo:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Al final de este código, *pop* restaura el estado de cada advertencia (incluye 4705, 4706 y 4707) al que tenía al principio del código.

Al escribir archivos de encabezado, puede usar *inserción* y *pop* para garantizar que los cambios de estado de advertencia realizados por un usuario no impiden que los encabezados de compilar correctamente. Use *inserción* al principio del encabezado y *pop* al final. Por ejemplo, si tiene un encabezado que no compila con limpieza en el nivel de advertencia 4, el código siguiente cambiaría el nivel de advertencia a 3 y después restablecería el nivel de advertencia original al final del encabezado.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Para obtener más información acerca del compilador de opciones que le ayudan a suprimen las advertencias, vea [/FI](../build/reference/fi-name-forced-include-file.md) y [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)