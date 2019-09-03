---
title: atributo de importación include ()
ms.date: 08/29/2019
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 39ab63525b2b83781cbcaf86a61742c5fb767b72
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218870"
---
# <a name="include-import-attribute"></a>atributo de importación include ()

**C++Cuestión**

Deshabilita la exclusión automática.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **include ("** _nombre1_ **"** [ __, "__ *nombre2* __"__ ...] __)__

### <a name="parameters"></a>Parámetros

*Nombre1*\
Primer elemento que se incluirá forzosamente.

*Nombre2*\
Segundo elemento que se incluirá forzosamente (si es necesario).

## <a name="remarks"></a>Comentarios

Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Si algunos elementos no deben excluirse automáticamente, es posible que vea [Advertencia del compilador (nivel 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md). Puede usar este atributo para deshabilitar la exclusión automática. Este atributo puede tomar cualquier número de argumentos, uno por cada nombre de un elemento de biblioteca de tipos que se va a incluir.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
