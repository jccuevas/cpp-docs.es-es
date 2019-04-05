---
title: Operadores de preprocesador
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 0b105cc2039e2aa50c11b796e5474a97d8c5c702
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035694"
---
# <a name="preprocessor-operators"></a>Operadores de preprocesador
Se utilizan cuatro operadores específicos del preprocesador en el contexto de la directiva `#define` (vea la lista siguiente para obtener un resumen de cada uno de ellos). En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token. Para obtener información sobre la `defined` operador, consulte [#if, #elif, #else y #endif directivas](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|Operador|Acción|
|--------------|------------|
|[Operador de generación de cadenas (#)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|
|[Operador de generación de caracteres (#@)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se delimite con comillas simples y se trate como un carácter (Específicos de Microsoft)|
|[Operador de pegado de token (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|
|[Operador defined](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)<br/>
[Macros predefinidas](../preprocessor/predefined-macros.md)<br/>
[Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)