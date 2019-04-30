---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383729"
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