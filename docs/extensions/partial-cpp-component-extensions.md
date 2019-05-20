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
ms.openlocfilehash: eb9b3907008147cb21f04aec5f42e4896fa35b3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516480"
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

### <a name="remarks"></a>Comentarios

Una clase parcial admite escenarios donde se modifica una parte de una definición de clase en un archivo y el software de generación automática de código, por ejemplo, el Diseñador XAML, modifica el código de la misma clase en otro archivo. Mediante una clase parcial, se puede evitar que el generador automático de código sobrescriba el código. En un proyecto de Visual Studio, el modificador **partial** se aplica automáticamente al archivo generado.

Contenido: Con dos excepciones, una definición de clase parcial puede contener todo lo que podría contener la definición de clase completa si se omitiera la palabra clave **partial**. Sin embargo, no se puede especificar la accesibilidad de clase (por ejemplo, `public partial class X { ... };`), o un elemento **declspec**.

Los especificadores de acceso usados en una definición de clase parcial para *identifier* no afectan a la accesibilidad predeterminada en una posterior definición de clase total o parcial de *identifier*. Se permiten definiciones insertadas de miembros de datos estáticos.

Declaración: una definición parcial de una clase *identifier* solo introduce el nombre *identifier*, pero *identifier* no se puede usar de forma que requiera una definición de clase. El nombre *identifier* no se puede usar para conocer el tamaño de *identifier*, ni para usar una base o miembro de *identifier* hasta que el compilador encuentre la definición completa de *identifier*.

Número y ordenación: Puede haber cero o más definiciones de clase parcial para *identifier*. Cada definición de clase parcial de *identifier* debe preceder léxicamente a la definición completa de *identifier* (si hay una definición completa; de lo contrario, la clase no se puede usar salvo si se declara adelantada), pero no debe preceder declaraciones adelantadas de *identifier*. Todas las claves de clase deben coincidir.

Definición completa: en el punto de la definición completa de la clase *identifier*, el comportamiento es el mismo que si la definición de *identifier* hubiera declarado todas las clases base, miembros, etc. en el orden en que se encontraron y definieron en las clases parciales.

Plantillas: una clase parcial no puede ser una plantilla.

Genéricos: una clase parcial puede ser un genérico si la definición completa puede ser genérica. Pero todas las clases parciales y totales deben tener exactamente los mismos parámetros genéricos, incluidos los nombres de parámetros formales.

Para más información sobre cómo usar la palabra clave **partial**, consulte [Clases parciales (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Esta característica del lenguaje no se aplica a Common Language Runtime).

## <a name="see-also"></a>Vea también

[Clases parciales (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)