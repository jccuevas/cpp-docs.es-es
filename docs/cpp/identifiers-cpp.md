---
title: Identificadores (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2b2c3899076206d3ce3b0094f3d85426bd321c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="identifiers-c"></a>Identificadores (C++)
Un identificador es una secuencia de caracteres que se usa para denotar:  
  
-   El nombre de un objeto o variable  
  
-   Un nombre de clase, estructura o unión  
  
-   Un nombre de tipo enumerado  
  
-   El miembro de una clase, estructura, unión o enumeración  
  
-   Una función o una función miembro de clase  
  
-   Un nombre de typedef  
  
-   Un nombre de etiqueta  
  
-   Un nombre de macro  
  
-   Un parámetro de macro  
  
 Los siguientes caracteres son válidos como cualquier carácter de un identificador:  
  
```  
_ a b c d e f g h i j k l m  
n o p q r s t u v w x y z  
A B C D E F G H I J K L M  
N O P Q R S T U V W X Y Z  
```  
  
 También se permiten determinados rangos de nombres de carácter universal en un identificador.  Un nombre de carácter universal en un identificador no puede designar un carácter de control ni un carácter en el juego de caracteres de origen básico. Para obtener más información, vea [Character Sets](../cpp/character-sets2.md). Estos rangos de números de punto de código Unicode son válidos como nombres de carácter universal para cualquier carácter de un identificador:  
  
-   00A8, 00AA, 00AD, 00AF, 00B2-00B5, 00B7-00BA, 00BC-00BE, 00C0-00D6, 00D8-00F6, 00F8-00FF, 0100-02FF, 0370-167F, 1681-180D, 180F-1DBF, 1E00-1FFF, 200B-200D, 202A-202E, 203F-2040, 2054, 2060-206F, 2070-20CF, 2100-218F, 2460-24FF, 2776-2793, 2C00-2DFF, 2E80-2FFF, 3004-3007, 3021-302F, 3031-303F, 3040-D7FF, F900-FD3D, FD40-FDCF, FDF0-FE1F, FE30-FE44, FE47-FFFD, 10000-1FFFD, 20000-2FFFD, 30000-3FFFD, 40000-4FFFD, 50000-5FFFD, 60000-6FFFD, 70000-7FFFD, 80000-8FFFD, 90000-9FFFD, A0000-AFFFD, B0000-BFFFD, C0000-CFFFD, D0000-DFFFD, E0000-EFFFD  
  
 Los siguientes caracteres son válidos para cualquier carácter de un identificador excepto el primero:  
  
```  
0 1 2 3 4 5 6 7 8 9  
```  
  
 Estos rangos de números de punto de código Unicode también son válidos como nombres de carácter universal para cualquier carácter de un identificador, excepto el primero:  
  
-   0300-036F, 1DC0-1DFF, 20D0-20FF, FE20-FE2F  
  
 **Específicos de Microsoft**  
  
 Solo los 2048 primeros caracteres de los identificadores de Microsoft C++ son significativos. El compilador hace que los nombres de los tipos definidos por el usuario sean "representativos" para conservar la información de tipo. El nombre resultante, incluida la información de tipo, no puede tener más de 2048 caracteres. (Consulte [nombres representativos](../build/reference/decorated-names.md) para obtener más información.) Los factores que pueden influir en la longitud de un identificador representativo son:  
  
-   Si el identificador indica un objeto de un tipo definido por el usuario o un tipo derivado de un tipo definido por el usuario.  
  
-   Si el identificador denota una función o un tipo derivado de una función.  
  
-   El número de argumentos para una función.  
  
 El signo de dólar `$` también es un identificador válido en Visual C++. Visual C++ también permite usar los caracteres reales representados por los rangos válidos de nombres de carácter universal en los identificadores. Para usar dichos caracteres, se debe guardar el archivo mediante una página de códigos para codificación de archivos que los incluya.  En este ejemplo muestra cómo dos caracteres extendidos y nombres de carácter universal se pueden usar indistintamente en el código.  
  
```  
// extended_identifier.cpp  
// In Visual Studio, use File, Advanced Save Options to set  
// the file encoding to Unicode codepage 1200  
struct テスト         // Japanese 'test'  
{  
    void トスト() {}  // Japanese 'toast'  
};  
  
int main() {  
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form  
    パン.トスト();        // compiler recognizes UCN or literal form  
}  
```  
  
 El rango de caracteres permitidos en un identificador es menos restrictivo cuando se compila código C++/CLI. Los identificadores del código compilado con /clr deben regirse por el  [Estándar ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 **FIN de Específicos de Microsoft**  
  
 El primer carácter de un identificador debe ser un carácter alfabético, en mayúsculas o minúsculas, o un carácter de subrayado ( **_** ). Debido a que los identificadores de C++ distinguen entre mayúsculas y minúsculas, `fileName` es diferente de `FileName`.  
  
 Los identificadores no pueden escribirse igual ni presentar el mismo uso de mayúsculas y minúsculas que las palabras clave. Los identificadores que contienen palabras clave son válidos. Por ejemplo, `Pint` es un identificador válido aunque contenga `int`, que es una palabra clave.  
  
 El uso de dos caracteres de subrayado secuenciales ( **__** ) al principio de un identificador o un único carácter de subrayado inicial seguido de una letra mayúscula se reserva para las implementaciones de C++ en todos los ámbitos. Evite el uso de un carácter de subrayado inicial seguido de una letra minúscula en los nombres con ámbito de archivo a fin de evitar posibles conflictos con los identificadores reservados actuales o futuros.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)