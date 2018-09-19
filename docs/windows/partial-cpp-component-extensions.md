---
title: Partial (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92fd30b0b420080d33f9938bec4891ac80ac660d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597083"
---
# <a name="partial--c-component-extensions"></a>partial (Extensiones de componentes de C++)

El **parcial** palabra clave permite a las distintas partes de la misma clase ref a crearse independientemente y en distintos archivos.

## <a name="all-runtimes"></a>Todos los runtimes

(Esta característica del lenguaje se aplica solo al tiempo de ejecución de Windows).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para una clase ref que tenga dos definiciones parciales, la **parcial** palabra clave se aplica a la primera aparición de la definición, y esto suele realizarla el código generado automáticamente, por lo que un humano codificador no usa la palabra clave muy a menudo. Para todas las definiciones parciales subsiguientes de la clase, omita el **parcial** modificador desde el *clave de la clase* identificador de palabra clave y la clase. Cuando el compilador encuentra una clase ref definido anteriormente y el identificador de clase pero no **parcial** palabra clave, internamente combina todas las partes de la definición de clase ref en una misma definición.

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

*clave de clase*  
Una palabra clave que declara una clase o struct que es compatible con el tiempo de ejecución de Windows. Cualquier **clase ref**, **clase de valor**, **ref struct**, o **struct de valor**.

*identifier*  
El nombre del tipo definido.

### <a name="remarks"></a>Comentarios

Una clase parcial es compatible con escenarios donde modifica una parte de una definición de clase en un archivo y el software de generación de código automática, por ejemplo, el Diseñador XAML, modifica el código en la misma clase en otro archivo. Mediante el uso de una clase parcial, puede impedir que el generador de código automática sobrescriba el código. En un proyecto de Visual Studio, el **parcial** modificador se aplica automáticamente al archivo generado.

Contenido: Con dos excepciones, una definición de clase parcial puede contener cualquier cosa que podría contener la definición de clase completa si el **parcial** se omite la palabra clave. Sin embargo, no se puede especificar la accesibilidad de clase (por ejemplo, `public partial class X { ... };`), o un **declspec**.

Obtener acceso a los especificadores que se utilizan en una definición de clase parcial para *identificador* no afectan a la accesibilidad predeterminada en una definición de clase parcial o completo posteriores *identificador*. Se permiten definiciones en línea de miembros de datos estáticos.

Declaración: Una definición parcial de una clase *identificador* solo introduce el nombre *identificador*, pero *identificador* no se puede usar de forma que requiere una clase definición. El nombre *identificador* no se puede usar para conocer el tamaño de *identificador*, o usar una base o miembro de *identificador* hasta después de que el compilador encuentra la definición completa de *identificador*.

Número y orden: puede haber cero o más definiciones de clase parcial para *identificador*. Todas las definiciones de clase parcial *identificador* debe preceder léxicamente a la definición completa de *identificador* (si hay una definición completa; en caso contrario, la clase no puede utilizarse con la excepción como si declarado de reenvío), pero no debe preceder a las declaraciones adelantadas de *identificador*. Deben coincidir con todas las "clase-claves".

Completa la definición: en el momento de la definición completa de la clase *identificador*, el comportamiento es el mismo como si la definición de *identificador* hubiera declarado todas las clases base, miembros, etc. en el orden en que se encontraron y se define en las clases parciales.

Plantillas: Una clase parcial no puede ser una plantilla.

Los genéricos: Una clase parcial puede ser un tipo genérico si la definición completa podría ser genérica. Pero todas las clases parciales y totales deben tener exactamente los mismos parámetros genéricos, incluidos los nombres de parámetros formales.

Para obtener más información sobre cómo usar el **parcial** palabra clave, consulte [clases parciales (C++ / c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Esta característica del lenguaje no se aplica a Common Language Runtime).

## <a name="see-also"></a>Vea también

[Las clases parciales (C++ / c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)