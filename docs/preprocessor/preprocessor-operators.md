---
title: Operadores de preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 5dd252fb495a05efe6eef45674f9ecd601a298a7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857949"
---
# <a name="preprocessor-operators"></a>Operadores de preprocesador

En el contexto de la Directiva `#define` se usan cuatro operadores específicos del preprocesador. Vea la tabla siguiente para obtener un resumen de cada uno de ellos. En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token. Para obtener información sobre el operador `defined`, vea [las directivas #if, #elif, #else y #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|"??"|Acción de|
|--------------|------------|
|[Operador de cadena (#)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|
|[Operador de carácter (# @)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se incluya entre comillas simples y se trate como un carácter (específico de Microsoft)|
|[Operador de pegado de token (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|
|[operador Defined](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
[Macros predefinidas](../preprocessor/predefined-macros.md)\
[Referencia del preprocesador de c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
