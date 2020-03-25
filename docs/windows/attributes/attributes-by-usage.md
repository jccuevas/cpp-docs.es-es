---
title: Atributos por uso
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: fd5c5826b4119409dd288d0587c3e53a7d3f3aab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167399"
---
# <a name="attributes-by-usage"></a>Atributos por uso

En este tema se enumeran los C++ atributos según los elementos del lenguaje a los que se aplican.

Si un atributo precede a un elemento que no está en el ámbito del atributo, el bloque de atributos se trata como un comentario.

|Atributo|Descripción|
|---------------|-----------------|
|[Atributos de módulo](module-attributes.md)|Se aplica al atributo [Module](module-cpp.md) .|
|[Atributos de interfaz](interface-attributes.md)|Se aplica a la palabra clave [__interface](../../cpp/interface.md) C++ .|
|[Atributos de clase](class-attributes.md)|Se aplica a C++ la palabra clave.|
|[Atributos de método](method-attributes.md)|Se aplica a los métodos de una clase, coclase o interfaz.|
|[Atributos de parámetro](parameter-attributes.md)|Se aplica a los parámetros de un método en una clase o interfaz.|
|[Atributos de miembros de datos](data-member-attributes.md)|Se aplica a los miembros de datos de una clase, coclase o interfaz.|
|[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)|Se aplica a C++ las palabras clave.|
|[Atributos de matriz](array-attributes.md)|Se aplica a las matrices o `SAFEARRAY`s.|
|[Atributos independientes](stand-alone-attributes.md)|Funciona más como una línea de código pero no funciona en una C++ palabra clave. Las instrucciones de atributo independientes requieren un punto y coma al final de la línea.|
|[Atributos personalizados](custom-attributes-cpp.md)|Permite al usuario extender los metadatos.|

## <a name="module-attributes"></a>Atributos de módulo
El atributo siguiente solo se puede aplicar al atributo [Module](module-cpp.md) .

|Atributo|Descripción|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se va a usar para realizar la búsqueda de cadenas de documento (localización).|

## <a name="interface-attributes"></a>Atributos de interfaz

Los siguientes atributos se aplican a la palabra clave [Interface (o __interface)](../../cpp/interface.md) C++ .

|Atributo|Descripción|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Especifica el UUID que dirige el compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.|
|[custom](custom-cpp.md)|Permite definir sus propios atributos.|
|[dispinterface](dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[dual](dual.md)|Coloca una interfaz en el archivo. idl como una interfaz dual.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo. hlp o. chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se va a usar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](hidden.md)|Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[local](local-cpp.md)|Permite usar el compilador MIDL como generador de encabezados cuando se usa en el encabezado de la interfaz. Cuando se usa en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonextensible](nonextensible.md)|Especifica que la implementación de `IDispatch` solo incluye las propiedades y los métodos enumerados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución. Este atributo solo es válido en una interfaz [dual](dual.md) .|
|[odl](odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[object](object-cpp.md)|Identifica una interfaz personalizada.|
|[oleautomation](oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[pointer_default](pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[restricted](restricted.md)|Designa a qué miembros de la biblioteca no se puede llamar arbitrariamente.|
|[uuid](uuid-cpp-attributes.md)|Proporciona el identificador único de la biblioteca.|

Debe observar estas reglas para definir una interfaz:

- La Convención de llamada predeterminada es [__stdcall](../../cpp/stdcall.md).

- Si no proporciona uno, se le proporciona un GUID.

- No se permite ningún método sobrecargado.

Cuando no se especifica el atributo [UUID](uuid-cpp-attributes.md) y se usa el mismo nombre de interfaz en distintos proyectos de atributos, se genera el mismo GUID.

## <a name="see-also"></a>Consulte también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)
