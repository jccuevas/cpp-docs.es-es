---
title: Atributos de compilador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29c58b94293ed00ba95d4288458788a0b2edd679
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601711"
---
# <a name="compiler-attributes"></a>Atributos de compilador

Los atributos de compilador proporcionan una variedad de funciones.

|Atributo|Descripción|
|---------------|-----------------|
|[emitidl](../windows/emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se coloca en el archivo .idl generado.|
|[event_receiver](../windows/event-receiver.md)|Crea un receptor de eventos.|
|[event_source](../windows/event-source.md)|Crea un origen de eventos.|
|[export](../windows/export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[Implementa](../windows/implements-cpp.md)|Especifica las interfaces de envío que se ven obligadas a ser miembros de la coclase IDL.|
|[importidl](../windows/importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado.|
|[importlib](../windows/importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[includelib](../windows/includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[library_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[no_injected_text](../windows/no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[satype](../windows/satype.md)|Especifica el tipo de datos de la `SAFEARRAY`.|
|[version](../windows/version-cpp.md)|Identifica una versión determinada entre varias versiones de una interfaz o clase.|

## <a name="see-also"></a>Vea también

[Atributos por grupo](../windows/attributes-by-group.md)