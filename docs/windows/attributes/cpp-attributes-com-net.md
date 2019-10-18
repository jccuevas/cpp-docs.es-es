---
title: Atributos de C++ para COM y .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 4885edf57988d5f83b56ba6a71da85877354d3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491052"
---
# <a name="c-attributes-for-com-and-net"></a>Atributos de C++ para COM y .NET

Microsoft define un conjunto de C++ atributos que simplifican la programación COM y .NET Framework Common Language Runtime desarrollo. Al incluir atributos en los archivos de código fuente, el compilador funciona con archivos dll de proveedor para insertar código o modificar el código de los archivos de objeto generados. Estos atributos ayudan en la creación de archivos. idl, interfaces, bibliotecas de tipos y otros elementos COM. En el entorno de desarrollo integrado (IDE), los atributos se admiten en los asistentes y en el ventana Propiedades.

Aunque los atributos eliminan parte de la codificación detallada necesaria para escribir objetos COM, se necesita un fondo en los [conceptos básicos de com](/windows/win32/com/the-component-object-model) para usarlos mejor.

> [!NOTE]
> Si busca atributos C++ estándar, vea [atributos](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Objetivo de los atributos

Los atributos C++ se extienden en direcciones que no son posibles actualmente sin interrumpir la estructura clásica del lenguaje. Los atributos permiten a los proveedores (DLL independientes) extender la funcionalidad de lenguaje de forma dinámica. El objetivo principal de los atributos es simplificar la creación de componentes COM, además de aumentar el nivel de productividad del desarrollador de componentes. Los atributos se pueden aplicar a casi C++ cualquier construcción, como clases, miembros de datos o funciones miembro. A continuación se incluye un resaltado de las ventajas que ofrece esta nueva tecnología:

- Expone una Convención de llamada sencilla y familiar.

- Utiliza el código insertado, que, a diferencia de las macros, es reconocido por el depurador.

- Permite la derivación sencilla de clases base sin ningún detalle de implementación.

- Reemplaza la gran cantidad de código IDL requerido por un componente COM con algunos atributos concisos.

Por ejemplo, para implementar un receptor de eventos simple para una clase ATL genérica, podría aplicar el atributo [event_receiver](event-receiver.md) a una clase específica como `CMyReceiver`. Después, el compilador de Microsoft C++ compila el atributo `event_receiver`, que inserta el código adecuado en el archivo objeto.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Después, puede configurar los métodos `CMyReceiver` `handler1` y `handler2` para controlar los eventos (mediante la función intrínseca [_ _ Hook](../../cpp/hook.md)) desde un origen de eventos, que se puede crear mediante [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Mecanismos básicos de los atributos

Hay tres maneras de insertar atributos en el proyecto. En primer lugar, puede insertarlos manualmente en el código fuente. En segundo lugar, puede insertarlos mediante la cuadrícula de propiedades de un objeto del proyecto. Por último, puede insertarlos con los distintos asistentes. Para obtener más información sobre el uso de la ventana **propiedades** y los distintos asistentes, vea [Visual Studio C++Projects- ](../../build/creating-and-managing-visual-cpp-projects.md).

Como antes, cuando se compila el proyecto, el compilador analiza C++ cada archivo de código fuente y genera un archivo objeto. Sin embargo, cuando el compilador encuentra un atributo, se analiza y comprueba sintácticamente. Después, el compilador llama dinámicamente a un proveedor de atributos para insertar código o realizar otras modificaciones en tiempo de compilación. La implementación del proveedor difiere en función del tipo de atributo. Por ejemplo, Atlprov. dll implementa los atributos relacionados con ATL.

En la siguiente ilustración se muestra la relación entre el compilador y el proveedor de atributos.

![Comunicación de atributo de componente](../media/vccompattrcomm.gif " de comunicación de atributo de componente")

> [!NOTE]
> El uso de atributos no modifica el contenido del archivo de código fuente. La única vez que el código de atributo generado es visible es durante las sesiones de depuración. Además, para cada archivo de código fuente del proyecto, puede generar un archivo de texto que muestre los resultados de la sustitución de atributos. Para obtener más información sobre este procedimiento, vea [/FX (combinar código insertado)](../../build/reference/fx-merge-injected-code.md) y [depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).

Como la C++ mayoría de las construcciones, los atributos tienen un conjunto de características que definen su uso correcto. Esto se conoce como el contexto del atributo y se trata en la tabla de contexto de atributo para cada tema de referencia de atributo. Por ejemplo, el atributo [CoClass](coclass.md) solo se puede aplicar a una clase o estructura existente, en lugar del atributo [cpp_quote](cpp-quote.md) , que se puede insertar en cualquier parte dentro C++ de un archivo de código fuente.

## <a name="building-an-attributed-program"></a>Compilar programas con atributos

Después de colocar los C++ atributos visuales en el código fuente, puede que desee que C++ el compilador de Microsoft genere una biblioteca de tipos y un archivo. idl. Las siguientes opciones del vinculador le ayudan a compilar archivos. tlb y. idl:

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Algunos proyectos contienen varios archivos. idl independientes. Se usan para generar dos o más archivos. tlb y, opcionalmente, enlazarlos en el bloque de recursos. Este escenario no se admite actualmente en Visual C++.

Además, el vinculador C++ visual generará toda la información de atributos relacionados con IDL en un solo archivo MIDL. No habrá forma de generar dos bibliotecas de tipos a partir de un único proyecto.

## <a name="contexts"></a>Contextos de atributo

C++los atributos se pueden describir con cuatro campos básicos: el destino al que se pueden aplicar (**se aplica a**), si son repetibles o no (**repetibles**), la presencia necesaria de otros atributos (**atributos requeridos**) e incompatibilidades. con otros atributos (**atributos no válidos**). Estos campos se muestran en una tabla adjunta en el tema de referencia de cada atributo. A continuación se describe cada uno de estos campos.

### <a name="applies-to"></a>Se aplica a

Este campo describe los distintos C++ elementos del lenguaje que son destinos válidos para el atributo especificado. Por ejemplo, si un atributo especifica "class" en el campo **se aplica a** , indica que el atributo solo se puede aplicar a una clase C++ válida. Si el atributo se aplica a una función miembro de una clase, se producirá un error de sintaxis.

Para obtener más información, vea [atributos por uso](attributes-by-usage.md).

### <a name="repeatable"></a>Reiterativo

Este campo indica si el atributo se puede aplicar varias veces al mismo destino. La mayoría de los atributos no se pueden repetir.

### <a name="required-attributes"></a>Atributos requeridos

Este campo muestra otros atributos que deben estar presentes (es decir, que se aplican al mismo destino) para que el atributo especificado funcione correctamente. No es habitual que un atributo tenga entradas para este campo.

### <a name="invalid-attributes"></a>Atributos no válidos

Este campo muestra otros atributos que no son compatibles con el atributo especificado. No es habitual que un atributo tenga entradas para este campo.

## <a name="in-this-section"></a>En esta sección

[Preguntas más frecuentes de programación con atributos](attribute-programming-faq.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Atributos por uso](attributes-by-usage.md)<br/>
[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)