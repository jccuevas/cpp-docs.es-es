---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216145"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++Cuestión**

Especifica otro prefijo para evitar conflictos de nombres.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **raw_method_prefix (** "*prefijo*" **)**

### <a name="parameters"></a>Parámetros

*Ceder*\
El prefijo que se va a usar.

## <a name="remarks"></a>Comentarios

Las propiedades y los métodos de bajo nivel se exponen mediante las funciones miembro denominadas con un prefijo predeterminado de **raw_** , para evitar conflictos de nombres con las funciones miembro de control de errores de alto nivel.

> [!NOTE]
> Los efectos del atributo **raw_method_prefix** no se modifican por la presencia del atributo [raw_interfaces_only](raw-interfaces-only.md) . **Raw_method_prefix** siempre tiene prioridad sobre `raw_interfaces_only` en la especificación de un prefijo. Si ambos atributos se utilizan en la misma `#import` instrucción, se usa el prefijo especificado por el atributo **raw_method_prefix** .

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
