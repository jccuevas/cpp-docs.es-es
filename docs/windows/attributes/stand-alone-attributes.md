---
title: Atributos independientes (COM de C++)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 1183d2b171a25b3b2d1aef14c19f81be65effc6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640834"
---
# <a name="stand-alone-attributes"></a>Atributos independientes

Un atributo independiente no funciona en una palabra clave de C++, pero es más parecido a una línea de código. Las instrucciones de atributo independiente requieren un punto y coma al final de la línea.

## <a name="stand-alone-attribute-list"></a>Lista de atributos independientes

|Atributo|Descripción|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo de encabezado generado.|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[emitidl](emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se coloca en el archivo .idl generado.|
|[idl_module](idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](idl-quote.md)|Le permite usar construcciones IDL que no se admiten en la versión actual de Visual C++ y pídales que pasen al archivo .idl generado.|
|[import](import.md)|Especifica otro archivo .idl, .odl o .h que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|
|[importidl](importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado|
|[importlib](importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[include](include-cpp.md)|Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.|
|[includelib](includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[pragma](pragma.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo .idl generado.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)