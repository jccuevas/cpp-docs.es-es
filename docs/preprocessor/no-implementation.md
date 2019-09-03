---
title: atributo de importación no_implementation
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220776"
---
# <a name="no_implementation-import-attribute"></a>atributo de importación no_implementation

**C++Cuestión**

Suprime la generación del `.tli` encabezado, que contiene las implementaciones de las funciones miembro del contenedor.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **no_implementation**

## <a name="remarks"></a>Comentarios

Si se especifica este atributo, el `.tlh` encabezado, con las declaraciones para exponer elementos de la biblioteca de tipos, se generará sin `#include` una instrucción para incluir `.tli` el archivo de encabezado.

Este atributo se usa junto con [implementation_only](../preprocessor/implementation-only.md).

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
