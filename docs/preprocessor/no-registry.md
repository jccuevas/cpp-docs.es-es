---
title: atributo de importación no_registry
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220725"
---
# <a name="no_registry-import-attribute"></a>atributo de importación no_registry

**no_registry** indica al compilador que no busque en el registro las bibliotecas `#import`de tipos importadas con.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **no_registry**

### <a name="parameters"></a>Parámetros

*Biblioteca de tipos*\
Una biblioteca de tipos.

## <a name="remarks"></a>Comentarios

Si no se encuentra una biblioteca de tipos a la que se hace referencia en los directorios de inclusión, se produce un error en la compilación incluso si la biblioteca de tipos está en el registro.  **no_registry** se propaga a otras bibliotecas de tipos importadas implícitamente con `auto_search`.

El compilador nunca busca en el registro las bibliotecas de tipos especificadas por el nombre de `#import`archivo y que se pasan directamente a.

Cuando `auto_search` se especifica, se generan `#import` las directivas adicionales mediante el valor de **no_registry** de la inicial `#import`. Si se `#import` **no_registry la**directiva inicial `#import` ,también se no_registry `auto_search`.

**no_registry** es útil si desea importar bibliotecas de tipos de referencias cruzadas. Impide que el compilador encuentre una versión anterior del archivo en el registro. **no_registry** también es útil si la biblioteca de tipos no está registrada.

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
