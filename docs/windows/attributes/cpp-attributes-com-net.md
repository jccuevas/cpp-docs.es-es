---
title: Atributos de C++ para COM y. NET | Microsoft Docs
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe6941e8809c0d735013b56d340f27302890b149
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792146"
---
# <a name="c-attributes-for-com-and-net"></a>Atributos de C++ para COM y .NET

Microsoft define un conjunto de atributos de C++ que simplifican la programación COM y el desarrollo de .NET Framework common language runtime. Al incluir atributos en los archivos de origen, el compilador funciona con archivos DLL para insertar código o modificar el código en los archivos objeto generados del proveedor. Estos atributos ayudan a la creación de otros elementos de COM, bibliotecas de tipos, interfaces y .idl (archivos). En el entorno de desarrollo integrado (IDE), se admiten atributos por los asistentes y la ventana Propiedades.

Aunque atributos eliminan parte del código detallado necesario para escribir objetos COM, que tiene un fondo en [Fundamentos de COM](/windows/desktop/com/the-component-object-model) para optimizar su uso.

> [!NOTE]
> Si busca atributos estándares de C++, vea [atributos](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Objetivo de los atributos

Atributos extensión C++ en direcciones no son actualmente posibles sin romper la estructura clásica del lenguaje. Los atributos permiten a proveedores (DLL independiente) para ampliar la funcionalidad del lenguaje dinámicamente. El objetivo principal de atributos es simplificar la creación de componentes COM, además de aumentar el nivel de productividad del desarrollador de componentes. Los atributos se pueden aplicar a casi cualquier construcción de C++, como clases, miembros de datos o las funciones miembro. Este es un área resaltada de ventajas que ofrece esta nueva tecnología:

- Expone una convención de llamada simple y familiar.

- Usa código insertado que, a diferencia de las macros, se reconoce el depurador.

- Permite la fácil derivación de clases base sin onerosos detalles de implementación.

- Reemplaza la gran cantidad de código IDL requerido por un componente COM con unos cuantos atributos concisos.

Por ejemplo, para implementar un receptor de eventos simple para una clase genérica de ATL, podría aplicar el [event_receiver](event-receiver.md) atributo en una clase específica como `CMyReceiver`. El `event_receiver` , a continuación, se compila el atributo por el compilador de Visual C++, que inserta el código adecuado en el archivo de objeto.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

A continuación, puede configurar el `CMyReceiver` métodos `handler1` y `handler2` para controlar los eventos (mediante la función intrínseca [__hook](../../cpp/hook.md)) desde un origen de eventos, puede crear mediante [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Mecanismos básicos de los atributos

Hay tres maneras de insertar atributos en el proyecto. En primer lugar, se puede insertarlos manualmente en el código fuente. En segundo lugar, puede insertarlos mediante la cuadrícula de propiedades de un objeto en el proyecto. Por último, puede insertarlos utilizando a los distintos asistentes. Para obtener más información sobre el uso de la **propiedades** ventana y los distintos asistentes, vea [crear y administrar proyectos de Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md).

Como antes, cuando se compila el proyecto, el compilador analiza cada archivo de origen de C++, generar un archivo de objeto. Sin embargo, cuando el compilador encuentra un atributo, se puede analizar y comprueba su sintaxis. A continuación, el compilador llama dinámicamente un proveedor de atributos para insertar código o realizar otras modificaciones en tiempo de compilación. La implementación del proveedor es diferente según el tipo de atributo. Por ejemplo, los atributos relacionados con ATL se implementan mediante Atlprov.dll.

En la siguiente ilustración se muestra la relación entre el compilador y el proveedor de atributos.

![Comunicación de atributos del componente](../media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> Uso de atributos no modifica el contenido del archivo de origen. Es el único momento en que el código generado del atributo está visible durante las sesiones de depuración. Además, para cada archivo de código fuente en el proyecto, puede generar un archivo de texto que muestra los resultados de la sustitución de atributos. Para obtener más información sobre este procedimiento, consulte [/Fx (combinar código insertado)](../../build/reference/fx-merge-injected-code.md) y [depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).

Al igual que la mayoría de las construcciones de C++, los atributos tienen un conjunto de características que define su uso correcto. Esto se conoce como el contexto del atributo y se trata en la tabla de contexto de atributo para cada tema de referencia de atributo. Por ejemplo, el [coclase](coclass.md) atributo solo puede aplicarse a una clase o estructura existente, en contraposición a la [cpp_quote](cpp-quote.md) atributo, que se puede insertar en cualquier lugar dentro de un archivo de código fuente de C++.

## <a name="building-an-attributed-program"></a>Compilar programas con atributos

Después de colocar los atributos de Visual C++ en el código fuente, puede el compilador de Visual C++ para generar un archivo .idl y de biblioteca de tipos para usted. Las siguiente opciones del vinculador ayudan a crear archivos .tlb y .idl:

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Algunos proyectos contienen varios archivos .idl independientes. Estos se usan para generar dos o más archivos .tlb y, opcionalmente, enlazarlos con el bloque de recursos. Este escenario no se admite actualmente en Visual C++.

Además, el vinculador de Visual C++ generarán toda la información de atributos relacionados con el IDL en un único archivo MIDL. No habrá ninguna manera de generar dos bibliotecas de tipos desde un solo proyecto.

## <a name="contexts"></a> Contextos de atributo

Atributos de C++ se pueden describir mediante los cuatro campos básicos: el destino se puede aplicar a (**se aplica a**), si son repetibles o no (**repetible**), el requiere la presencia de otros atributos ( **Atributos requeridos**) y las incompatibilidades con otros atributos (**atributos no válidos**). Estos campos se muestran en una tabla que aparece en el tema de referencia de cada atributo. Cada uno de estos campos se describe a continuación.
  
### <a name="applies-to"></a>Se aplica a

Este campo describe los diferentes elementos del lenguaje C++ que son destinos válidos para el atributo especificado. Por ejemplo, si un atributo especifica "class" en la **se aplica a** campo, esto indica que el atributo solo puede aplicarse a una clase de C++ válida. Si el atributo se aplica a una función miembro de una clase, se produciría un error de sintaxis.
  
Para obtener más información, consulte [atributos por uso](attributes-by-usage.md).
  
### <a name="repeatable"></a>Reiterativo

Este campo indica si el atributo puede aplicarse varias veces en el mismo destino. La mayoría de los atributos no son repetibles.
  
### <a name="required-attributes"></a>Atributos requeridos

Este campo muestra otros atributos que deben estar presentes (que es, se aplican al mismo destino) para el atributo especificado funcionar correctamente. Es raro que un atributo para que todas las entradas para este campo.
  
### <a name="invalid-attributes"></a>Atributos no válidos

Este campo muestra otros atributos que no son compatibles con el atributo especificado. Es raro que un atributo para que todas las entradas para este campo.

## <a name="in-this-section"></a>En esta sección

[Preguntas más frecuentes de programación con atributos](attribute-programming-faq.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Atributos por uso](attributes-by-usage.md)<br/>
[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)