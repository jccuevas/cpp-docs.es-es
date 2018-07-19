---
title: -EN EL MONTÓN | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /heap
dev_langs:
- C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5306df647801d7d1467aa0f44bfacca18fccaff3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372222"
---
# <a name="heap"></a>/HEAP
Establece el tamaño del montón en bytes. Esta opción solo se aplica a los archivos ejecutables.  
  
```  
  
/HEAP:  
reserve[,commit]  
```  
  
## <a name="remarks"></a>Comentarios  
 El `reserve` argumento especifica la asignación del montón inicial total de memoria virtual. De forma predeterminada, el tamaño del montón es 1 MB. [Referencia de EDITBIN](../../build/reference/editbin-reference.md) se redondea el valor especificado al múltiplo más próximo de 4 bytes.  
  
 Opcional `commit` argumento está sujeto a interpretación por el sistema operativo. En un sistema operativo Windows, especifica la cantidad inicial de memoria física para asignar y la cantidad de memoria adicional para asignar cuando se debe expandir el montón. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Una mayor `commit` valor permite al sistema de asignar memoria menor a menudo, cuando la aplicación necesite más espacio del montón, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio de la aplicación. El `commit` valor debe ser menor o igual que el `reserve` valor.  
  
 Especifique el `reserve` y `commit` valores en formato decimal o notación del lenguaje c. octal o hexadecimal. Por ejemplo, puede especificarse un valor de 1 MB como 1048576 en formato decimal, o como 0 x 100000 en formato hexadecimal o como 04000000 en octal.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)