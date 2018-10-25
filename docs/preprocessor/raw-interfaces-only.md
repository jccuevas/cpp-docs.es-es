---
title: raw_interfaces_only | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 789c9179b2ba48f5c3796f709931728bc756aaaa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075039"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Específicos de C++**

Suprime la generación de funciones de contenedor de control de errores y [propiedad](../cpp/property-cpp.md) declaraciones que utilizan esas funciones de contenedor.

## <a name="syntax"></a>Sintaxis

```
raw_interfaces_only
```

## <a name="remarks"></a>Comentarios

El **raw_interfaces_only** atributo también hace que el prefijo predeterminado utilizado en la nomenclatura de las funciones que no son propiedad va a quitar. Normalmente, el prefijo es **raw_**. Si se especifica este atributo, los nombres de función pertenecen directamente a la biblioteca de tipos.

Este atributo permite exponer solo el contenido de bajo nivel de la biblioteca de tipos.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)