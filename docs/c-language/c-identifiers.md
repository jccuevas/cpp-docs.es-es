---
title: Identificadores de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: fca83b12e469401fe18632a1df9f876964b8a493
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="c-identifiers"></a>Identificadores de C
Los "identificadores" o "símbolos" son los nombres que se proporcionan para variables, tipos, funciones y etiquetas del programa. Los nombres de identificadores deben diferir en ortografía y mayúsculas y minúsculas de cualquier palabra clave. No se puede utilizar palabras clave (ya sea de C o de Microsoft) como identificadores; se reservan para uso especial. Para crear un identificador, especifíquelo en la declaración de una variable, un tipo o una función. En este ejemplo, `result` es un identificador para una variable de tipo entero y `main` y `printf` son nombres de identificador para funciones.  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
 Una vez declarado, puede utilizar el identificador en instrucciones de programa posteriores para hacer referencia al valor asociado.  
  
 Una clase especial de identificador, denominada una etiqueta de instrucción, se puede utilizar en instrucciones `goto`. (Las declaraciones se describen en [Declaraciones y tipos](../c-language/declarations-and-types.md). Las etiquetas de instrucción se describen en [Instrucciones goto y con etiquetas](../c-language/goto-and-labeled-statements-c.md)).  
  
## <a name="syntax"></a>Sintaxis  
 *identifier*:  
 *nondigit*  
  
 *identifier nondigit*  
  
 *identifier digit*  
  
 `nondigit`: uno de  
 **_ a b c d e f g h i j k l m n o p q r s t u v w x y z**  
  
 **A B C D E F G H I J K L M N O P Q R S T U V W X Y Z**  
  
 `digit`: uno de  
 **0 1 2 3 4 5 6 7 8 9**  
  
 El primer carácter de un nombre de identificador debe ser `nondigit` (es decir, el primer carácter debe ser un subrayado o una letra mayúscula o minúscula). ANSI permite seis caracteres significativos en el nombre de un identificador externo y 31 para los nombres de identificadores internos (dentro de una función). Los identificadores externos (los declarados en el ámbito global o declarados con la clase de almacenamiento `extern`) pueden estar sujetos a restricciones de nomenclatura adicionales, porque estos identificadores se tienen que procesar con otro software, tal como vinculadores.  
  
 **Específicos de Microsoft**  
  
 Aunque ANSI permite 6 caracteres significativos en nombres de identificador externo y 31 para nombres de identificadores internos (dentro de una función), Microsoft C permite 247 caracteres de un nombre de identificador interno o externo. Si no le preocupa la compatibilidad ANSI, puede modificar este valor predeterminado a un número menor o mayor mediante la opción /H (restringir la longitud de nombres externos).  
  
 **FIN de Específicos de Microsoft**  
  
 El compilador de C considera que las mayúsculas y las minúsculas son caracteres distintos. Esta característica, denominada "distinción entre mayúsculas y minúsculas", permite crear identificadores distintos que tienen la misma ortografía pero distintas mayúsculas y minúsculas. Por ejemplo, cada uno de los identificadores siguientes es único:  
  
```  
add  
ADD  
Add  
aDD  
```  
  
 **Específicos de Microsoft**  
  
 No seleccione nombres de identificadores que comiencen con dos caracteres de subrayado o con un subrayado seguido por una letra mayúscula. El estándar ANSI C permite nombres de identificador que comiencen con estas combinaciones de caracteres que se reservan para el uso del compilador. Los identificadores con ámbito de nivel de archivo tampoco deben nombrarse con un carácter de subrayado y una minúscula como dos primeras letras. Los nombres de identificador que comienzan con estos caracteres también están reservados. Por convención, Microsoft utiliza un subrayado y una letra mayúscula para iniciar los nombres de macro y caracteres de subrayado dobles para los nombres de palabras clave específicas de Microsoft. Para evitar cualquier conflicto de nombres, seleccione siempre nombres de identificador que no comiencen por uno o dos caracteres de subrayado o nombres que comiencen por un carácter de subrayado seguido por una letra mayúscula.  
  
 **FIN de Específicos de Microsoft**  
  
 Los siguientes son ejemplos de identificadores válidos que cumplen las restricciones de nomenclatura de ANSI o Microsoft:  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
 **Específicos de Microsoft**  
  
 Aunque los identificadores de los archivos de código fuente distinguen entre mayúsculas y minúsculas de forma predeterminada, los símbolos de los archivos de objetos no lo hacen. Microsoft C trata los identificadores de una unidad de compilación distinguiendo entre mayúsculas y minúsculas.  
  
 El vinculador de Microsoft distingue entre mayúsculas y minúsculas. Debe especificar todos los identificadores de manera coherente en cuando a mayúsculas y minúsculas.  
  
 El "juego de caracteres de origen" es el juego de caracteres válidos que pueden aparecer en archivos de código fuente. Para Microsoft C, el juego de origen es el juego de caracteres ASCII estándar. El juego de caracteres de origen y el juego de caracteres de ejecución incluyen los caracteres ASCII utilizados como secuencias de escape. Vea [Constantes de caracteres](../c-language/c-character-constants.md) para obtener información sobre el juego de caracteres de ejecución.  
  
 **FIN de Específicos de Microsoft**  
  
 Un identificador tiene "ámbito", que es la región de programa en el que se conoce y "vinculación", que determina si el mismo nombre en otro ámbito hace referencia al mismo identificador. Estos temas se explican en [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md).  
  
## <a name="see-also"></a>Vea también  
 [Elementos de C](../c-language/elements-of-c.md)
