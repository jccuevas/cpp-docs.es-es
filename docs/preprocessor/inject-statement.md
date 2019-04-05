---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034292"
---
# <a name="injectstatement"></a>inject_statement

**Específicos de C++**

Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```
inject_statement("source_text")
```

### <a name="parameters"></a>Parámetros

*source_text*<br/>
Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.

## <a name="remarks"></a>Comentarios

El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)