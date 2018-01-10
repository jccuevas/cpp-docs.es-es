---
title: execution_character_set | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs: C++
helpviewer_keywords: pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1064f5cf97ba6b919e718c60c8346e86d643ced
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="executioncharacterset"></a>execution_character_set
Especifica el juego de caracteres de ejecución utilizado para los literales de cadena y carácter. Esta directiva no es necesaria para los literales marcados con el prefijo u8.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `target`  
 Especifica el juego de caracteres de ejecución de destino. Actualmente la ejecución de destino solo establecer admitida es "utf-8".  
  
## <a name="remarks"></a>Comentarios  
 Esta directiva de compilador es obsoleta a partir de Visual Studio 2015 Update 2. Se recomienda que realice la **/execution-charset:utf-8** o **/utf-8** opciones del compilador junto con utilizando el `u8` prefijo en estrecha caracteres y cadenas literales que contienen extendidos caracteres. Para obtener más información sobre la `u8` prefix, consulte [literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md). Para obtener más información acerca de las opciones del compilador, vea [/execution-charset (establecer el juego de caracteres en la ejecución)](../build/reference/execution-charset-set-execution-character-set.md) y [/utf-8 (establecer origen y ejecutable juegos a UTF-8 de caracteres)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).  
  
 El `#pragma execution_character_set("utf-8")` directiva indica al compilador para codificar caracteres estrechos y literales de cadena estrechos en el código fuente como UTF-8 en el archivo ejecutable. Esta codificación de salida es independiente de la codificación de archivos de origen utilizada.  
  
 De forma predeterminada, el compilador codifica caracteres estrechos y cadenas de caracteres estrechos mediante la página de códigos actual como el juego de caracteres de ejecución. Esto significa que los caracteres Unicode o DBCS en un literal que están fuera del intervalo de la página de códigos actual se convierten en el carácter de reemplazo predeterminado en la salida. Los caracteres Unicode y DBCS se truncan en su byte de orden inferior. Esto seguramente no es lo que deseado. Puede especificar la codificación UTF-8 para los valores literales en el archivo de origen mediante el uso de un `u8` prefijo. El compilador pasa estas cadenas con codificación UTF-8 a la salida sin cambios. Literales de caracteres estrechos como precedidos utilizando u8 deben caber en un byte, o que se trunquen en la salida.  
  
 De forma predeterminada, Visual Studio usa la página de códigos actual como el juego de caracteres de origen utilizado para interpretar el código fuente para la salida. Cuando se lee un archivo en, Visual Studio lo interpreta según la página de códigos actual a menos que se estableció la página de códigos del archivo, o una marca de orden de bytes (BOM) o caracteres UTF-16 se detectan al principio del archivo. Dado que UTF-8 no se puede establecer como la página de códigos actual, cuando la detección automática encuentra archivos de código fuente que se codifica como UTF-8 sin una marca BOM, Visual Studio se da por supuesto que se codifican mediante el uso de la página de códigos actual. Caracteres en el archivo de origen que se encuentra fuera del intervalo del elemento especificado o automáticamente detectan página de códigos puede provocar errores y advertencias del compilador.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/Execution-CharSet (establecer el juego de caracteres en la ejecución)](../build/reference/execution-charset-set-execution-character-set.md)   
 [/UTF-8 (establecer origen y el ejecutable juegos de caracteres UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)