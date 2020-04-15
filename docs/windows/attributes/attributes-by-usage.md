---
title: Atributos por uso
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361332"
---
# <a name="attributes-by-usage"></a>Atributos por uso

En este tema se enumeran los atributos según los elementos de lenguaje C++ a los que se aplican.

Si un atributo precede a un elemento que no está en el ámbito del atributo, el bloque de atributos se trata como un comentario.

|Atributo|Descripción|
|---------------|-----------------|
|[Atributos del módulo](module-attributes.md)|Se aplica al atributo [module.](module-cpp.md)|
|[Atributos de interfaz](interface-attributes.md)|Se aplica a la palabra clave [__interface](../../cpp/interface.md) C++..|
|[Atributos de clase](class-attributes.md)|Se aplica a la palabra clave C++.|
|[Atributos del método](method-attributes.md)|Se aplica a los métodos de una clase, coclase o interfaz.|
|[Atributos de parámetro](parameter-attributes.md)|Se aplica a los parámetros de un método en una clase o interfaz.|
|[Atributos de miembros de datos](data-member-attributes.md)|Se aplica a los miembros de datos de una clase, coclase o interfaz.|
|[Atributos Typedef, Enum, Union y Struct](typedef-enum-union-and-struct-attributes.md)|Se aplica a las palabras clave C++.|
|[Atributos de matriz](array-attributes.md)|Se aplica a `SAFEARRAY`matrices o s.|
|[Atributos independientes](stand-alone-attributes.md)|Funciona más como una línea de código, pero no funciona en una palabra clave C++. Las instrucciones de atributo independientes requieren un punto y coma al final de la línea.|
|[Atributos personalizados](custom-attributes-cpp.md)|Permite al usuario ampliar los metadatos.|

## <a name="module-attributes"></a>Atributos de módulo

El siguiente atributo solo se puede aplicar al atributo [module.](module-cpp.md)

|Atributo|Descripción|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se usará para realizar la búsqueda de cadenas de documento (localización).|

## <a name="interface-attributes"></a>Atributos de interfaz

Los siguientes atributos se aplican a la [interfaz (o __interface)](../../cpp/interface.md) palabra clave C++.

|Atributo|Descripción|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Especifica el UUID que dirige al compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.|
|[Personalizado](custom-cpp.md)|Le permite definir sus propios atributos.|
|[Dispinterface](dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[Doble](dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|
|[exportar](export.md)|Hace que una estructura de datos se coloque en el archivo .idl.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de ayuda.|
|[Helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o .chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se usará para realizar la búsqueda de cadenas de documento (localización).|
|[Oculto](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo .idl.|
|[local](local-cpp.md)|Le permite utilizar el compilador MIDL como generador de encabezados cuando se utiliza en el encabezado de interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se generan códigos auxiliares.|
|[nonextensible](nonextensible.md)|Especifica que `IDispatch` la implementación incluye solo las propiedades y métodos enumerados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución. Este atributo solo es válido en una interfaz [dual.](dual.md)|
|[Odl](odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[object](object-cpp.md)|Identifica una interfaz personalizada.|
|[oleautomation](oleautomation.md)|Indica que una interfaz es compatible con Automation.|
|[pointer_default](pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[Ptr](ptr.md)|Designa un puntero como puntero completo.|
|[Restringido](restricted.md)|Designa qué miembros de la biblioteca no se pueden llamar arbitrariamente.|
|[uuid](uuid-cpp-attributes.md)|Proporciona el identificador único para la biblioteca|

Usted debe observar estas reglas para definir una interfaz:

- La convención de llamada predeterminada es [__stdcall](../../cpp/stdcall.md).

- Se proporciona un GUID si no proporciona uno.

- No se permiten métodos sobrecargados.

Cuando no se especifica el atributo [uuid](uuid-cpp-attributes.md) y se usa el mismo nombre de interfaz en diferentes proyectos de atributo, se genera el mismo GUID.

## <a name="see-also"></a>Consulte también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)
