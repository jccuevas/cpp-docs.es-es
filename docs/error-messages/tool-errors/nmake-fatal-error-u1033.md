---
title: Error grave de NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173392"
---
# <a name="nmake-fatal-error-u1033"></a>Error grave de NMAKE U1033

error de sintaxis: ' cadena ' inesperada

La cadena no forma parte de la sintaxis válida para un archivo make.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Si el conjunto de corchetes angulares ( **<<** ) de un archivo insertado no se encuentra al principio de una línea, se produce el siguiente error:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Si una definición de macro en el archivo make contenía un signo igual ( **=** ) sin un nombre anterior o si el nombre que se está definiendo es una macro que se expande a nada, se produce el siguiente error:

    ```
    syntax error : '=' unexpected
    ```

1. Si el punto y coma ( **;** ) en una línea de comentario en herramientas. INI no se encuentra al principio de la línea, se produce el siguiente error:

    ```
    syntax error : ';' unexpected
    ```

1. Si un procesador de textos ha dado formato al archivo make, puede producirse el siguiente error:

    ```
    syntax error : ':' unexpected
    ```
