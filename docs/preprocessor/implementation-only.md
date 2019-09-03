---
title: atributo de importación implementation_only
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218976"
---
# <a name="implementation_only-import-attribute"></a>atributo de importación implementation_only

**C++Cuestión**

Suprime la generación del archivo `.tlh` de encabezado principal de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **implementation_only**

## <a name="remarks"></a>Comentarios

Este archivo contiene todas las declaraciones utilizadas para exponer el contenido de la biblioteca de tipos. El `.tli` archivo de encabezado, con las implementaciones de las funciones miembro de contenedor, se generará e incluirá en la compilación.

Cuando se especifica este atributo, el contenido del `.tli` encabezado está en el mismo espacio de nombres que el que se usa normalmente en el `.tlh` encabezado. Además, las funciones miembro no se declaran como alineadas.

El atributo **implementation_only** está pensado para su uso junto con el atributo [no_implementation](../preprocessor/no-implementation.md) como una manera de mantener las implementaciones fuera del archivo de encabezado precompilado (PCH). Una instrucción `#import` con el atributo `no_implementation` se coloca en la región de origen usada para crear el PCH. Varios archivos de código fuente utilizan el PCH resultante. Después `#import` , se usa una instrucción con el atributo **implementation_only** fuera de la región PCH. Solo es necesario usar esta instrucción una vez en uno de los archivos de código fuente. Genera todas las funciones miembro de contenedor necesarias sin volver a compilaciones adicionales para cada archivo de código fuente.

> [!NOTE]
> El atributo **implementation_only** de una `#import` instrucción debe usarse junto con otra `#import` instrucción, de la misma biblioteca de tipos, con el `no_implementation` atributo. De lo contrario, se generan errores del compilador. Esto se debe a que las definiciones de clase `#import` de contenedor generadas por la instrucción con el `no_implementation` atributo son necesarias para compilar las implementaciones generadas por el atributo **implementation_only** .

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
