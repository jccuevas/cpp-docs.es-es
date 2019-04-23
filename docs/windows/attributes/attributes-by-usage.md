---
title: Atributos por uso
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: f6567a7866516c09bca03fa9f3d3aa5aa997b6b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038075"
---
# <a name="attributes-by-usage"></a>Atributos por uso

En este tema se enumera los atributos en función de los elementos del lenguaje C++ a la que se aplican.

Si un atributo precede a un elemento que no está en el ámbito del atributo, el bloque de atributos se trata como un comentario.

|Atributo|Descripción|
|---------------|-----------------|
|[Atributos de módulo](module-attributes.md)|Se aplica a la [módulo](module-cpp.md) atributo.|
|[Atributos de interfaz](interface-attributes.md)|Se aplica a la [__interface](../../cpp/interface.md) C++ palabra clave.|
|[Atributos de clase](class-attributes.md)|Se aplica a la palabra clave de C++.|
|[Atributos de método](method-attributes.md)|Se aplica a los métodos en una clase, coclase o interfaz.|
|[Atributos de parámetro](parameter-attributes.md)|Se aplica a los parámetros de un método en una clase o interfaz.|
|[Atributos de miembros de datos](data-member-attributes.md)|Se aplica a los miembros de datos en una clase, coclase o interfaz.|
|[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)|Se aplica a las palabras clave de C++.|
|[Atributos de matriz](array-attributes.md)|Se aplica a las matrices o `SAFEARRAY`s.|
|[Atributos independientes](stand-alone-attributes.md)|Actúa más como una línea de código, pero no funciona en una palabra clave de C++. Las instrucciones de atributo independiente requieren un punto y coma al final de la línea.|
|[Atributos personalizados](custom-attributes-cpp.md)|Permite al usuario extender los metadatos.|

## <a name="module-attributes"></a>Atributos de módulo
Solo se puede aplicar el atributo siguiente a la [módulo](module-cpp.md) atributo.

|Atributo|Descripción|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|

## <a name="interface-attributes"></a>Atributos de interfaz

Los siguientes atributos se aplican a la [interfaz (o __interface)](../../cpp/interface.md) C++ palabra clave.

|Atributo|Descripción|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.|
|[custom](custom-cpp.md)|Le permite definir sus propios atributos.|
|[dispinterface](dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[dual](dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[local](local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonextensible](nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y los métodos enumeran en la descripción de la interfaz y no se pueden ampliar con miembros adicionales en tiempo de ejecución. Este atributo solo es válido en un [dual](dual.md) interfaz.|
|[odl](odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[object](object-cpp.md)|Identifica una interfaz personalizada.|
|[oleautomation](oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[pointer_default](pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[restricted](restricted.md)|Designa qué miembros de la biblioteca no se puede llamar arbitrariamente.|
|[uuid](uuid-cpp-attributes.md)|Proporciona el identificador único para la biblioteca|

Se deben observar estas reglas para definir una interfaz:

- Convención de llamada predeterminada es [__stdcall](../../cpp/stdcall.md).

- Si no se proporciona, se proporciona un GUID para usted.

- No se permiten métodos sobrecargados.

Al no especificar el [uuid](uuid-cpp-attributes.md) atributo y con el mismo nombre de interfaz en los proyectos de atributo diferente, se genera el mismo GUID.

## <a name="see-also"></a>Vea también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)