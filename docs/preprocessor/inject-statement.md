---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: cf7d06eddb5ae6d08f57fb82613d97c7dcc36074
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566717"
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)