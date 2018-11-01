---
title: Atributos de compilador (COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792134"
---
# <a name="compiler-attributes"></a>Atributos de compilador

Los atributos de compilador proporcionan una variedad de funciones.

|Atributo|Descripción|
|---------------|-----------------|
|[emitidl](emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se coloca en el archivo .idl generado.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[Implementa](implements-cpp.md)|Especifica las interfaces de envío que se ven obligadas a ser miembros de la coclase IDL.|
|[importidl](importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado.|
|[importlib](importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[includelib](includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[satype](satype.md)|Especifica el tipo de datos de la `SAFEARRAY`.|
|[version](version-cpp.md)|Identifica una versión determinada entre varias versiones de una interfaz o clase.|

## <a name="see-also"></a>Vea también

[Atributos por grupo](attributes-by-group.md)