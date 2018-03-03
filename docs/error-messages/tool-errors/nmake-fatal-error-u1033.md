---
title: Error grave de NMAKE U1033 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94f2626e1ce318d83d306595e386f880c62dec3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1033"></a>Error grave de NMAKE U1033
error de sintaxis: 'cadena' inesperado  
  
 La cadena no es parte de la sintaxis válida de un archivo MAKE.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Si establece el cierre de corchetes angulares (**<<**) para un archivo en línea no están al principio de una línea, se produce el siguiente error:  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Si una definición de macro en el archivo MAKE contiene un signo igual (**=**) sin nombre a una anterior o si el nombre que se define es una macro que se expande a nada, se produce el siguiente error:  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  Si el punto y coma (**;**) en una línea de comentario de herramientas. INI no está al principio de la línea, se produce el siguiente error:  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  Si se ha formateado previamente el archivo MAKE por un procesador de textos, puede producirse el error siguiente:  
  
    ```  
    syntax error : ':' unexpected  
    ```