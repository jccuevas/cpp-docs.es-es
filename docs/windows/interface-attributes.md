---
title: Atributos de la interfaz | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f57cdce20a54b8bc56b804e12f59f92855c7f69
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880210"
---
# <a name="interface-attributes"></a>Atributos de interfaz
Los siguientes atributos se aplican a la [interface (o __interface)](../cpp/interface.md) palabra clave de C++.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|Especifica el UUID que hace que el compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.|  
|[Personalizada](../windows/custom-cpp.md)|Le permite definir sus propios atributos.|  
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|  
|[dual](../windows/dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|  
|[export](../windows/export.md)|Hace que una estructura de datos que se colocarán en el archivo IDL.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|  
|[helpfile](../windows/helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se utiliza para describir el elemento al que se aplica.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre de la DLL a utilizar para realizar la búsqueda de cadena de documento (localización).|  
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador orientado al usuario.|  
|[library_block](../windows/library-block.md)|Coloca una construcción en bloque de biblioteca del archivo .idl.|  
|[Local](../windows/local-cpp.md)|Permite usar el compilador MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|  
|[nonextensible](../windows/nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y métodos aparecen en la descripción de interfaz y no se puede ampliar con miembros adicionales en tiempo de ejecución. Este atributo solo es válido en una [dual](../windows/dual.md) interfaz.|  
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|  
|[object](../windows/object-cpp.md)|Identifica una interfaz personalizada.|  
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con la automatización.|  
|[pointer_default](../windows/pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros excepto los punteros de nivel superior que aparecen en las listas de parámetros.|  
|[ptr](../windows/ptr.md)|Designa un puntero como un puntero completo.|  
|[restricted](../windows/restricted.md)|Indica qué miembros de la biblioteca no se puede llamar de forma arbitraria.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Proporciona el identificador único de la biblioteca|  
  
 Se deben observar estas reglas para definir una interfaz:  
  
-   Convención de llamada predeterminada es [__stdcall](../cpp/stdcall.md).  
  
-   Un GUID se proporciona automáticamente si no se proporciona.  
  
-   No hay ningún método sobrecargado se permite.  
  
 Al no especificar el [uuid](../windows/uuid-cpp-attributes.md) de atributo y con el mismo nombre de interfaz en los proyectos de atributo diferente, se genera el mismo GUID.  
  
## <a name="see-also"></a>Vea también  
 [Atributos por uso](../windows/attributes-by-usage.md)