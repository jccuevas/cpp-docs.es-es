---
title: "Operador de conversi&#243;n a cadenas (#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "# (operador de preprocesador)"
  - "argumentos [C++], convertir a cadenas"
  - "macros [C++], convertir parámetros a cadenas"
  - "preprocesador"
  - "preprocesador, operadores"
  - "literales de cadena, convertir parámetros de macro a"
  - "stringizing (operador)"
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Operador de conversi&#243;n a cadenas (#)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de signo de número o de "generación de cadenas" \(**\#**\) convierte parámetros de macro en literales de cadena sin expandir la definición del parámetro.  Se utiliza únicamente con las macros que toman argumentos.  Si precede un parámetro formal en la definición de macro, el argumento real pasado por la llamada de macro se pone entre comillas y se trata como un literal de cadena.  El literal de cadena reemplaza cada aparición de una combinación de operador de generación de cadenas y parámetro formal dentro de la definición de macro.  
  
> [!NOTE]
>  Ya no se admite la extensión de Microsoft C \(versión 6.0 y anteriores\) para el estándar ANSI C que expandía los argumentos formales de macro que aparecían dentro de literales de cadena y constantes de caracteres.  El código que dependía de esta extensión se debe volver a escribir mediante el operador de generación de cadenas \(**\#**\).  
  
 No se tiene en cuenta el espacio en blanco que precede al primer token del argumento real y que va detrás del último token del argumento real.  Cualquier espacio en blanco entre los tokens del argumento real se reduce a un único espacio en blanco en el literal de cadena resultante.  Así, si se incluye un comentario entre dos tokens en el argumento real, se reduce a un único espacio en blanco.  El literal de cadena resultante se concatena automáticamente con cualquier literal de cadena adyacente del que esté separado solo por espacio en blanco.  
  
 Además, si un carácter contenido en el argumento normalmente requiere una secuencia de escape cuando se utiliza en un literal de cadena \(por ejemplo, las comillas dobles \(**"**\) o la barra diagonal inversa \(**\\**\)\), se insertará automáticamente la secuencia de escape de barra diagonal inversa antes del carácter.  
  
 Es posible que el operador de generación de cadenas de Visual C\+\+ no se comporte como se espera en todas las situaciones; vea [16.3.2 El operador \#](../misc/16-3-2-the-hash-operator.md) para obtener más información.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una definición de macro que incluye el operador de generación de cadenas y una función principal que invoca la macro:  
  
 Tales invocaciones se expandirían durante el preprocesamiento, y generarían el código siguiente:  
  
```  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
  **In quotes in the printf function call**  
**"In quotes when printed to the screen"**  
**"This: \\"  prints an escaped double quote"**   
## Ejemplo  
 En el ejemplo siguiente se muestra cómo se puede expandir un parámetro de macro:  
  
```  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)