---
title: Error grave de NMAKE U1033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066389"
---
# <a name="nmake-fatal-error-u1033"></a>Error grave de NMAKE U1033

error de sintaxis: 'cadena' inesperado

La cadena no es parte de la sintaxis válida para un archivo MAKE.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Si establece el cierre de corchetes angulares (**<<**) para un archivo en línea no están al principio de una línea, se produce el error siguiente:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Si una definición de macro en el archivo MAKE contiene un signo igual (**=**) sin nombre a una anterior o si el nombre que se define es una macro que se expande a nada, se produce el error siguiente:

    ```
    syntax error : '=' unexpected
    ```

1. Si el punto y coma (**;**) en una línea de comentario en las herramientas. INI no está al principio de la línea, se produce el error siguiente:

    ```
    syntax error : ';' unexpected
    ```

1. Si el archivo MAKE se ha dado formato mediante un procesador de textos, puede producirse el error siguiente:

    ```
    syntax error : ':' unexpected
    ```