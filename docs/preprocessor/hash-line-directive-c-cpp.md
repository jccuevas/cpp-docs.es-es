---
title: "#<a name=\"line-directive-cc--microsoft-docs\"></a>línea directiva (C/C ++) | Documentos de Microsoft"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#line'
dev_langs: C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38006dcb6438ca05f6a310dc5e470f5bbd083c43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="line-directive-cc"></a>#line (Directiva) (C/C++)

La directiva `#line` indica al preprocesador que cambie el número de línea y el nombre de archivo almacenados internamente por el compilador a un número de línea y un nombre de archivo especificados.

## <a name="syntax"></a>Sintaxis

> **#line** *secuencia de dígitos* ["*filename*"]

## <a name="remarks"></a>Comentarios

El compilador utiliza el número de línea y el nombre de archivo opcional para hacer referencia a los errores que encuentra durante la compilación. El número de línea suele referirse a la línea de entrada actual, y el nombre de archivo hace referencia al archivo de entrada actual. El número de línea se incrementa una vez que se procesa cada línea.

El *secuencia de dígitos* valor puede ser cualquier constante entera. El reemplazo de macros se pueden realizar en los tokens de preprocesamiento, pero el resultado debe evaluarse como la sintaxis correcta. El *filename* puede ser cualquier combinación de caracteres y deben incluirse entre comillas dobles (**""**). Si *filename* es se omite, el nombre de archivo anterior permanece sin cambios.

Se puede cambiar el número de línea y el nombre de archivo de código fuente mediante una directiva `#line`. El traductor usa el número de línea y el nombre de archivo para determinar los valores de las macros predefinidas **&#95; &#95; ARCHIVO de &#95; &#95;**  y **&#95; &#95; LÍNEA &#95; &#95;** . Estas macros se pueden utilizar para insertar mensajes de error autodescriptivos en el texto del programa. Para obtener más información sobre estas macros predefinidas, vea [Macros predefinidas](../preprocessor/predefined-macros.md).

El **&#95; &#95; ARCHIVO de &#95; &#95;**  macro se expande a una cadena cuyo contenido es el nombre de archivo entrecomillado comillas dobles (**""**).

Si se cambia el número de línea y el nombre de archivo, el compilador omite los valores anteriores y continúa el procesamiento con los nuevos valores. Los generadores de programas suelen emplear la directiva `#line` para hacer que los mensajes de error hagan referencia al archivo de código fuente original en lugar de al programa generado.

Los ejemplos siguientes ilustran `#line` y **&#95; &#95; LÍNEA &#95; &#95;**  y **&#95; &#95; ARCHIVO de &#95; &#95;**  macros.

En esta declaración, el número de línea almacenado internamente se establece en 151 y el nombre de archivo se cambia a copy.c.

```cpp
#line 151 "copy.c"
```

 En este ejemplo, la macro `ASSERT` utiliza las macros predefinidas **&#95; &#95; LÍNEA &#95; &#95;**  y **&#95; &#95; ARCHIVO de &#95; &#95;**  para imprimir un mensaje de error sobre el archivo de origen si no se cumple una aserción determinada.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)