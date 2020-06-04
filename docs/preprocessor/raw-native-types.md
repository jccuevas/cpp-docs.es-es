---
title: atributo de importación raw_native_types
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216073"
---
# <a name="raw_native_types-import-attribute"></a>atributo de importación raw_native_types

**C++Cuestión**

Deshabilita el uso de clases de compatibilidad con COM en las funciones contenedoras de alto nivel y fuerza el uso de tipos de datos de bajo nivel en su lugar.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **raw_native_types**

## <a name="remarks"></a>Comentarios

De forma predeterminada, los métodos de control de errores de alto nivel usan las clases de compatibilidad con com [_ bstr_t](../cpp/bstr-t-class.md) y `BSTR` [_ variant_t](../cpp/variant-t-class.md) en lugar de los tipos de datos y `VARIANT` y los punteros de interfaz com sin formato. Estas clases encapsulan los detalles de asignación y desasignación del almacenamiento de memoria para estos tipos de datos, y simplifican considerablemente la conversión de tipos y las operaciones de conversión.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
