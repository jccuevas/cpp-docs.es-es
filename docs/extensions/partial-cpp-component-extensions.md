---
title: partial (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: ad8faa08a2c85e777cbc8721e5842e708b9e6cb1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181855"
---
# <a name="partial--ccli-and-ccx"></a>partial (C++/CLI y C++/CX)

La palabra clave **partial** permite que diferentes partes de la misma clase de referencia se creen de forma independiente y en archivos diferentes.

## <a name="all-runtimes"></a>Todos los runtimes

(Esta característica de lenguaje solo se aplica a Windows Runtime).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para que una clase de referencia tenga dos definiciones parciales, la palabra clave **partial** se aplica a la primera aparición de la definición, y esto se realiza normalmente mediante código generado automáticamente, por lo que un codificador humano no usará la palabra clave muy a menudo. En todas las definiciones parciales subsiguientes de la clase, omita el modificador **partial** de la palabra clave *class-key* y el identificador de clase. Cuando el compilador encuentra una clase de referencia y un identificador de clase definidos previamente pero ninguna palabra clave **partial**, combina internamente todas las partes de la definición de clase referencia en una misma definición.

### <a name="syntax"></a>Sintaxis

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>Parámetros

*class-key*<br/>
Una palabra clave que declara una clase o un struct que se admite en Windows Runtime. **ref class**, **value class**, **ref struct** o **value struct**.

*identifier*<br/>
El nombre del tipo definido.

### <a name="remarks"></a>Observaciones

Una clase parcial admite escenarios donde se modifica una parte de una definición de clase en un archivo y el software de generación automática de código, por ejemplo, el Diseñador XAML, modifica el código de la misma clase en otro archivo. Mediante una clase parcial, se puede evitar que el generador automático de código sobrescriba el código. En un proyecto de Visual Studio, el modificador **partial** se aplica automáticamente al archivo generado.

Contenido: con dos excepciones, una definición de clase parcial puede contener todo lo que la definición de clase completa podría contener si se omitiera la palabra clave **partial** . Sin embargo, no se puede especificar la accesibilidad de clase (por ejemplo, `public partial class X { ... };`), o un elemento **declspec**.

Los especificadores de acceso usados en una definición de clase parcial para *identifier* no afectan a la accesibilidad predeterminada en una posterior definición de clase total o parcial de *identifier*. Se permiten definiciones insertadas de miembros de datos estáticos.

Declaración: una definición parcial de un *identificador* de clase solo introduce el *identificador*de nombre, pero el *identificador* no se puede usar de forma que requiera una definición de clase. El nombre *identifier* no se puede usar para conocer el tamaño de *identifier*, ni para usar una base o miembro de *identifier* hasta que el compilador encuentre la definición completa de *identifier*.

Número y ordenación: puede haber cero o más definiciones de clase parcial para el *identificador*. Cada definición de clase parcial de *identifier* debe preceder léxicamente a la definición completa de *identifier* (si hay una definición completa; de lo contrario, la clase no se puede usar salvo si se declara adelantada), pero no debe preceder declaraciones adelantadas de *identifier*. Todas las claves de clase deben coincidir.

Definición completa: en el punto de la definición completa del *identificador*de clase, el comportamiento es el mismo que si la definición de *identificador* hubiera declarado todas las clases base, miembros, etc. en el orden en que se encontraron y se definieron en las clases parciales.

Plantillas: una clase parcial no puede ser una plantilla.

Genéricos: una clase parcial puede ser genérica si la definición completa puede ser genérica. Pero todas las clases parciales y totales deben tener exactamente los mismos parámetros genéricos, incluidos los nombres de parámetros formales.

Para más información sobre cómo usar la palabra clave **partial**, consulte [Clases parciales (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Esta característica del lenguaje no se aplica a Common Language Runtime).

## <a name="see-also"></a>Consulte también

[Clases parciales (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
