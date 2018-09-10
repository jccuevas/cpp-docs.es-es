---
title: Atributos de interfaz | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 850646e2dda1f226eff7c921dd3fe9f85595ca69
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317659"
---
# <a name="interface-attributes"></a>Atributos de interfaz

Los siguientes atributos se aplican a la [interfaz (o __interface)](../cpp/interface.md) palabra clave de C++.

|Atributo|Descripción|
|---------------|-----------------|
|[async_uuid](../windows/async-uuid.md)|Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.|
|[Personalizado](../windows/custom-cpp.md)|Le permite definir sus propios atributos.|
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[dual](../windows/dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|
|[export](../windows/export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|
|[helpfile](../windows/helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[library_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[local](../windows/local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonextensible](../windows/nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y los métodos enumeran en la descripción de la interfaz y no se pueden ampliar con miembros adicionales en tiempo de ejecución. Este atributo solo es válido en un [dual](../windows/dual.md) interfaz.|
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[object](../windows/object-cpp.md)|Identifica una interfaz personalizada.|
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[pointer_default](../windows/pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[ptr](../windows/ptr.md)|Designa un puntero como un puntero completo.|
|[restricted](../windows/restricted.md)|Designa qué miembros de la biblioteca no se puede llamar arbitrariamente.|
|[uuid](../windows/uuid-cpp-attributes.md)|Proporciona el identificador único para la biblioteca|

Se deben observar estas reglas para definir una interfaz:

- Convención de llamada predeterminada es [__stdcall](../cpp/stdcall.md).

- Si no se proporciona, se proporciona un GUID para usted.

- No se permiten métodos sobrecargados.

Al no especificar el [uuid](../windows/uuid-cpp-attributes.md) atributo y con el mismo nombre de interfaz en los proyectos de atributo diferente, se genera el mismo GUID.

## <a name="see-also"></a>Vea también

[Atributos por uso](../windows/attributes-by-usage.md)