---
title: Atributos independientes (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166177"
---
# <a name="stand-alone-attributes"></a>Atributos independientes

Un atributo independiente no funciona en una C++ palabra clave, pero es más similar a una línea de código. Las instrucciones de atributo independientes requieren un punto y coma al final de la línea.

## <a name="stand-alone-attribute-list"></a>Lista de atributos independientes

|Atributo|Descripción|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Emite la cadena especificada, sin los caracteres de Comillas, en el archivo de encabezado generado.|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[emitidl](emitidl.md)|Determina si todos los atributos IDL subsiguientes se procesarán y colocarán en el archivo. idl generado.|
|[idl_module](idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](idl-quote.md)|Permite usar construcciones IDL que no se admiten en la versión actual de Visual C++ y hacer que pasen al archivo. idl generado.|
|[import](import.md)|Especifica otro archivo. idl,. ODL o. h que contiene las definiciones a las que se desea hacer referencia desde el archivo. idl principal.|
|[importidl](importidl.md)|Inserta el archivo. idl especificado en el archivo. idl generado.|
|[importlib](importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[include](include-cpp.md)|Especifica uno o más archivos de encabezado que se van a incluir en el archivo. idl generado.|
|[includelib](includelib-cpp.md)|Hace que un archivo. idl o. h se incluya en el archivo. idl generado.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador Inserte código como resultado del uso de atributos.|
|[pragma](pragma.md)|Emite la cadena especificada, sin los caracteres de Comillas, en el archivo. idl generado.|

## <a name="see-also"></a>Consulte también

[Atributos por uso](attributes-by-usage.md)
