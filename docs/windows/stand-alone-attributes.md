---
title: Atributos independientes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d395053231f54570e1bf86ba79f6237b89681fc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315553"
---
# <a name="stand-alone-attributes"></a>Atributos independientes
Un atributo independiente no funciona en una palabra clave de C++, pero es más parecido a una línea de código. Las instrucciones de atributo independiente requieren un punto y coma al final de la línea.
  
|Atributo|Descripción|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo de encabezado generado.|
|[Personalizado](../windows/custom-cpp.md)|Le permite definir su propio atributo.|
|[db_command](../windows/db-command.md)|Crea un comando OLE DB.|
|[emitidl](../windows/emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se coloca en el archivo .idl generado.|
|[idl_module](../windows/idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](../windows/idl-quote.md)|Le permite usar construcciones IDL que no se admiten en la versión actual de Visual C++ y pídales que pasen al archivo .idl generado.|
|[import](../windows/import.md)|Especifica otro archivo .idl, .odl o .h que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|
|[importidl](../windows/importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado|
|[importlib](../windows/importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[include](../windows/include-cpp.md)|Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.|
|[includelib](../windows/includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[library_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[módulo](../windows/module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[no_injected_text](../windows/no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[pragma](../windows/pragma.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo .idl generado.|
  
## <a name="see-also"></a>Vea también
 [Atributos por uso](../windows/attributes-by-usage.md)