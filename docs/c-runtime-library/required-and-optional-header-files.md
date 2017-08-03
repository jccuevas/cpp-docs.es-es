---
title: Archivos de encabezado requeridos y opcionales | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.headers
dev_langs:
- C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 82f325ec2a8e928d721b3b3f16683961634365e2
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="required-and-optional-header-files"></a>Archivos de encabezado requeridos y opcionales
La descripción de cada rutina de tiempo de ejecución incluye una lista de archivos de encabezado (.H) requeridos y opcionales para dicha rutina. Los archivos de encabezado requeridos deben incluirse para obtener la declaración de función de la rutina o una definición utilizada por otra rutina a la que se llama internamente. Los archivos de encabezado opcionales se suelen incluir para aprovechar las ventajas de las contantes, las definiciones de tipo o las macros alineadas predefinidas. En la tabla siguiente se indican algunos ejemplos de contenido de los archivos de encabezado opcionales:  
  
|Definición|Ejemplo|  
|----------------|-------------|  
|Definición de macro|Si una rutina de la biblioteca se implementa como una macro, la definición de macro puede estar en un archivo de encabezado que no sea el archivo de encabezado de la rutina original. Por ejemplo, la macro `_toupper` está definida en el archivo de encabezado CTYPE.H, mientras que la función `toupper` está declarada en STDLIB.H.|  
|Constante predefinida|Muchas rutinas de la biblioteca hacen referencia a las constantes que se definen en archivos de encabezado. Por ejemplo, la rutina `_open` utiliza constantes como `_O_CREAT`, que se define en el archivo de encabezado FCNTL.H.|  
|Definición de tipo|Algunas rutinas de la biblioteca devuelven una estructura o adoptan una estructura como argumento. Por ejemplo, las rutinas de entrada/salida de secuencias utilizan una estructura de tipo `FILE`, que se define en STDIO.H.|  
  
 Los archivos de encabezado de la biblioteca en tiempo de ejecución proporcionan declaraciones de función en el estilo recomendado de ANSI/ISO C estándar. El compilador realiza la comprobación de tipos en cualquier referencia a rutinas que se produce después de su declaración de función asociada. Las declaraciones de función son especialmente importantes para las rutinas que devuelven un valor de algún tipo distinto de `int`, que es el valor predeterminado. El compilador considerará como valor devuelvo `int` en caso de que las rutinas no especifiquen su valor devuelto apropiado en su declaración, un comportamiento que puede generar resultados inesperados. Vea [Comprobación de tipos](../c-runtime-library/type-checking-crt.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
