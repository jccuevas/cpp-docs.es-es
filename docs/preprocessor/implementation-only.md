---
title: implementation_only
ms.date: 11/04/2016
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: c1435ca74ac2b5a73c308592b1affe6fca097d1b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026661"
---
# <a name="implementationonly"></a>implementation_only
**Específicos de C++**

Suprime la generación de archivos de encabezado .tlh (el archivo de encabezado principal).

## <a name="syntax"></a>Sintaxis

```
implementation_only
```

## <a name="remarks"></a>Comentarios

Este archivo contiene todas las declaraciones utilizadas para exponer el contenido de la biblioteca de tipos. El archivo de encabezado .tli, con las implementaciones de las funciones miembro del contenedor, se genera y se incluye en la compilación.

Cuando se especifica este atributo, el contenido del encabezado .tli está en el mismo espacio de nombres que el utilizado normalmente en el encabezado .tlh. Además, las funciones miembro no se declaran como alineadas.

El **implementation_only** atributo está pensado para su uso junto con el [no_implementation](../preprocessor/no-implementation.md) atributo como una manera de mantener las implementaciones fuera del archivo de encabezado precompilado (PCH). Una instrucción `#import` con el atributo `no_implementation` se coloca en la región de origen usada para crear el PCH. Varios archivos de código fuente utilizan el PCH resultante. Un `#import` instrucción con el **implementation_only** , a continuación, se usa el atributo fuera de la región PCH. Debe usar esta instrucción una sola vez en uno de los archivos de código fuente. Esto generará todas las funciones miembro del contenedor necesarias sin necesidad de recompilación adicional para cada archivo de código fuente.

> [!NOTE]
> El **implementation_only** atributo en uno `#import` instrucción debe usarse junto con otra `#import` instrucción de la misma biblioteca de tipos, con el `no_implementation` atributo. De lo contrario, se generarán errores de compilador. Esto es porque las definiciones de clase de contenedor generan por el `#import` instrucción con el `no_implementation` atributo son necesarias para compilar las implementaciones generadas por el **implementation_only** atributo.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)