---
title: Atributos independientes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59846b1ca031cc02c85cb6ace23f96e8c5cc9f37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890441"
---
# <a name="stand-alone-attributes"></a>Atributos independientes
Un atributo independiente no funciona en una palabra clave de C++, pero es más parecido a una línea de código. Las instrucciones de atributo independiente requieren un punto y coma al final de la línea.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|[cpp_quote](../windows/cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas, en el archivo de encabezado generado.|  
|[Personalizada](../windows/custom-cpp.md)|Le permite definir su propio atributo.|  
|[db_command](../windows/db-command.md)|Crea un comando OLE DB.|  
|[emitidl](../windows/emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se colocan en el archivo .idl generado.|  
|[idl_module](../windows/idl-module.md)|Especifica un punto de entrada en un archivo DLL.|  
|[idl_quote](../windows/idl-quote.md)|Le permite usar las construcciones de IDL no se admiten en la versión actual de Visual C++ y pídale que pasen al archivo .idl generado.|  
|[import](../windows/import.md)|Especifica otro archivo .idl, .odl o .h que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|  
|[importidl](../windows/importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado|  
|[importlib](../windows/importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|  
|[include](../windows/include-cpp.md)|Especifica uno o más archivos de encabezado que se incluirá en el archivo .idl generado.|  
|[includelib](../windows/includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|  
|[library_block](../windows/library-block.md)|Coloca una construcción en bloque de biblioteca del archivo .idl.|  
|[Módulo](../windows/module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|  
|[no_injected_text](../windows/no-injected-text.md)|Evita que el compilador inserte código como resultado del uso de atributos.|  
|[pragma](../windows/pragma.md)|Emite la cadena especificada, sin los caracteres de comillas, en el archivo .idl generado.|  
  
## <a name="see-also"></a>Vea también  
 [Atributos por uso](../windows/attributes-by-usage.md)