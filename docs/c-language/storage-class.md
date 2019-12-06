---
title: Clase de almacenamiento
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: aa6e977b3aa03b5f08901cfa8b0abe1b4046e72d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857013"
---
# <a name="storage-class"></a>Clase de almacenamiento

El especificador de clase de almacenamiento en una definición de función proporciona a la función la clase de almacenamiento `extern` o **static**.

## <a name="syntax"></a>Sintaxis

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *Attribute-SEQ* es un \*específico de Microsoft /

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*storage-class-specifier*: /\* Para definiciones de función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**

Si una definición de función no incluye el elemento *storage-class-specifier*, la clase de almacenamiento utiliza `extern` de forma predeterminada. Puede declarar explícitamente una función como `extern`, pero no es necesario.

Si la declaración de una función contiene el elemento *storage-class-specifier* `extern`, el identificador tiene la misma vinculación que cualquier declaración visible del identificador con ámbito de archivo. Si no hay ninguna declaración visible con ámbito de archivo, el identificador tiene una vinculación externa. Si un identificador tiene ámbito de archivo pero ningún especificador *storage-class-specifier*, el identificador tiene una vinculación externa. Vinculación externa significa que cada instancia del identificador designa el mismo objeto o función. Vea [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md) para obtener más información sobre la vinculación y el ámbito de archivo.

Las declaraciones de función de ámbito de bloque con un especificador de clase de almacenamiento distinto de `extern` generan errores.

Una función con clase de almacenamiento **static** solo es visible en el archivo de código fuente en el que se define. Todas las demás funciones, se les asigne la clase de almacenamiento `extern` de forma explícita o implícita, están visibles en todos los archivos de código fuente del programa. Si se desea la clase de almacenamiento **static**, esta debe declararse en la primera aparición de una declaración (si existe) de la función, y en la definición de la función.

**Específicos de Microsoft**

Cuando las extensiones de Microsoft están habilitadas, una función declarada originalmente sin una clase de almacenamiento o con la clase de almacenamiento `extern` tiene la clase de almacenamiento **static** si la definición de función está en el mismo archivo de código fuente y si la definición especifica explícitamente la clase de almacenamiento **static**.

Al compilar con la opción del compilador /Ze, las funciones declaradas dentro de un bloque mediante la palabra clave `extern` tienen visibilidad global. Esto no es cierto cuando se compila con /Za. No debe confiar en esta característica si la portabilidad del código fuente es importante.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Definiciones de función de C](../c-language/c-function-definitions.md)
