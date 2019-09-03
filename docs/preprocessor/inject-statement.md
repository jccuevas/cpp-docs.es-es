---
title: atributo de importación inject_statement
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220993"
---
# <a name="inject_statement-import-attribute"></a>atributo de importación inject_statement

**C++Cuestión**

Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **inject_statement (** "*texto de origen*" **)**

### <a name="parameters"></a>Parámetros

*texto de origen*\
Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.

## <a name="remarks"></a>Comentarios

El texto se coloca al principio de la declaración de espacio de nombres que contiene el contenido de la *biblioteca de tipos* en el archivo de encabezado.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
