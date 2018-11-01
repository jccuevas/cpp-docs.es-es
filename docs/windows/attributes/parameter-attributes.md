---
title: Atributos de parámetro (COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], parameter attributes
- parameter attributes
ms.assetid: 024c2dd5-49d7-4ced-a17a-c56c1bc485b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 160e71111a9080367390302a59c41a53580ffe0b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792137"
---
# <a name="parameter-attributes"></a>Atributos de parámetro

Los siguientes atributos se aplican a los parámetros de un método en una clase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[Personalizado](custom-cpp.md)|Le permite definir su propio atributo.|
|[defaultvalue](defaultvalue.md)|Permite especificar un valor predeterminado para un parámetro opcional con tipo.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[iid_is](iid-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[immediatebind](immediatebind.md)|Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.|
|[in](in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.|
|[last_is](last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|
|[lcid](lcid.md)|Le permite pasar un identificador de configuración regional a una función.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se transmitan.|
|[max_is](max-is.md)|Designa el valor máximo para un índice de matriz válida.|
|[Opcional](optional-cpp.md)|Especifica un parámetro opcional para una función miembro.|
|[out](out-cpp.md)|Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|
|[intervalo](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[ref](ref-cpp.md)|Identifica un puntero de referencia.|
|[retval](retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|
|[satype](satype.md)|Especifica el tipo de datos de la `SAFEARRAY` estructura.|
|[size_is](size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo - o matrices multidimensionales.|
|[unique](unique-cpp.md)|Especifica un puntero único.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)