---
title: atributo de importación raw_interfaces_only
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216211"
---
# <a name="raw_interfaces_only-import-attribute"></a>atributo de importación raw_interfaces_only

**C++Cuestión**

Suprime la generación de funciones contenedoras de control de errores y declaraciones de [propiedad](../cpp/property-cpp.md) que utilizan esas funciones contenedoras.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **raw_interfaces_only**

## <a name="remarks"></a>Comentarios

El atributo **raw_interfaces_only** también hace que se quite el prefijo predeterminado usado para asignar nombres a las funciones que no son de propiedad. Normalmente, el prefijo `raw_`es. Si se especifica este atributo, los nombres de función se toman directamente de la biblioteca de tipos.

Este atributo permite exponer solo el contenido de bajo nivel de la biblioteca de tipos.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
