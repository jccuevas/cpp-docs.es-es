---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028265"
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

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)