---
title: no_registry
ms.date: 10/18/2018
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 2a0fd9a761f765aa9562ab18c095f683b80c7987
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411323"
---
# <a name="noregistry"></a>no_registry

**no_registry** indica al compilador que no busque en el registro bibliotecas de tipos importadas con `#import`.

## <a name="syntax"></a>Sintaxis

```
#import filename no_registry
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Una biblioteca de tipos.

## <a name="remarks"></a>Comentarios

Si no se encuentra una biblioteca de tipos que se hace referencia en los directorios de inclusión, se producirá un error en la compilación incluso si la biblioteca de tipos está en el registro.  **no_registry** se propaga a otras bibliotecas de tipos importadas implícitamente con `auto_search`.

El compilador nunca buscará en el registro bibliotecas de tipos especificadas por nombre de archivo y que se hayan pasado directamente a `#import`.

Cuando `auto_search` se especifica, el adicionales `#import`s se generará con el **no_registry** configuración de la inicial `#import` (si inicial `#import` directiva fue **no_registry** , un `auto_search`-genera `#import` también es **no_registry**.)

**no_registry** es útil si desea importar bibliotecas de tipo de referencia sin el riesgo de que el compilador encuentre una versión anterior del archivo en el registro. **no_registry** también es útil si la biblioteca de tipos no está registrada.

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)