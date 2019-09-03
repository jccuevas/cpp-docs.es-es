---
title: Operadores de preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 1c556e4af5913ba8d0dc7efc9648e0d0004d9d7e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222254"
---
# <a name="preprocessor-operators"></a>Operadores de preprocesador

Se utilizan cuatro operadores específicos del preprocesador en el contexto de la `#define` Directiva. Vea la tabla siguiente para obtener un resumen de cada uno de ellos. En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token. Para obtener información sobre `defined` el operador, vea [las directivas #if, #elif, #else y #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|Operador|.|
|--------------|------------|
|[Operador de cadena (#)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|
|[Operador de carácter (# @)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se delimite con comillas simples y se trate como un carácter (Específicos de Microsoft)|
|[Operador de pegado de token (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|
|[operador Defined](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
[Macros predefinidas](../preprocessor/predefined-macros.md)\
[Referencia del preprocesador de c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
