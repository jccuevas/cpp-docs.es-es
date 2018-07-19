---
title: Generación de cadenas (#) de operador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7891b03fe80b5ad91ad52cf4577d237350d4584c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841704"
---
# <a name="stringizing-operator-"></a>Operador de conversión a cadenas (#)
El operador "generación de cadenas" o un signo de número (**#**) convierte parámetros de macro en literales de cadena sin expandir la definición del parámetro. Se utiliza únicamente con las macros que toman argumentos. Si precede un parámetro formal en la definición de macro, el argumento real pasado por la llamada de macro se pone entre comillas y se trata como un literal de cadena. El literal de cadena reemplaza cada aparición de una combinación de operador de generación de cadenas y parámetro formal dentro de la definición de macro.  
  
> [!NOTE]
>  Ya no se admite la extensión de Microsoft C (versión 6.0 y anteriores) para el estándar ANSI C que expandía los argumentos formales de macro que aparecían dentro de literales de cadena y constantes de caracteres. El código que dependía de esta extensión se debe reescribir mediante la generación de cadenas (**#**) operador.  
  
No se tiene en cuenta el espacio en blanco que precede al primer token del argumento real y que va detrás del último token del argumento real. Cualquier espacio en blanco entre los tokens del argumento real se reduce a un único espacio en blanco en el literal de cadena resultante. Así, si se incluye un comentario entre dos tokens en el argumento real, se reduce a un único espacio en blanco. El literal de cadena resultante se concatena automáticamente con cualquier literal de cadena adyacente del que esté separado solo por espacio en blanco.  
  
Además, si un carácter contenido en el argumento normalmente requiere una secuencia de escape cuando se utiliza en un literal de cadena (por ejemplo, las comillas (**"**) o barra diagonal inversa (**\\**) caracteres), el barra diagonal inversa de escape necesarias se inserta automáticamente antes del carácter.  
  
El operador de generación de cadenas de Visual C++ no se comporten correctamente cuando se utiliza con cadenas que incluyen secuencias de escape. En esta situación, el compilador genera [C2017 de Error del compilador](../error-messages/compiler-errors-1/compiler-error-c2017.md).  
  
## <a name="example"></a>Ejemplo  
En el ejemplo siguiente se muestra una definición de macro que incluye el operador de generación de cadenas y una función principal que invoca la macro:  
  
Tales invocaciones se expandirían durante el preprocesamiento, y generarían el código siguiente:  
  
```cpp  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```cpp  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
```Output  
In quotes in the printf function call  
"In quotes when printed to the screen"  
"This: \"  prints an escaped double quote"  
```  
  
## <a name="example"></a>Ejemplo  
En el ejemplo siguiente se muestra cómo se puede expandir un parámetro de macro:  
  
```cpp  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## <a name="see-also"></a>Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)