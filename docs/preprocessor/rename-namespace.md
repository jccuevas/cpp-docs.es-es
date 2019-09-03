---
title: atributo de importación rename_namespace
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216656"
---
# <a name="rename_namespace-import-attribute"></a>atributo de importación rename_namespace

**C++Cuestión**

Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **rename_namespace (** "*NewName*" **)**

### <a name="parameters"></a>Parámetros

*NewName*\
Nuevo nombre del espacio de nombres.

## <a name="remarks"></a>Comentarios

El atributo **rename_namespace** toma un solo argumento, *NewName*, que especifica el nuevo nombre del espacio de nombres.

Para quitar el espacio de nombres, use el atributo [no_namespace](../preprocessor/no-namespace.md) en su lugar.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
