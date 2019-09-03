---
title: atributo de importación no_dual_interfaces
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220760"
---
# <a name="no_dual_interfaces-import-attribute"></a>atributo de importación no_dual_interfaces

**C++Cuestión**

Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **no_dual_interfaces**

## <a name="remarks"></a>Comentarios

Normalmente, el contenedor llama al método a través de la tabla de funciones virtuales de la interfaz. Con **no_dual_interfaces**, en su lugar, el `IDispatch::Invoke` contenedor llama a para invocar el método.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
