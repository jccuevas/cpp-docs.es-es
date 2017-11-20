---
title: Campos de bits de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ebc62a975e534d89fd99dbb05a65e8d6cb379bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-bit-fields"></a>Campos de bits de C
Además de los declaradores para los miembros de una estructura o unión, un declarador de estructura también puede ser un número especificado de bits, denominado un "campo de bits". Su longitud se establece en el declarador del nombre de campo mediante un signo de dos puntos. Un campo de bits se interpreta como un tipo entero.  
  
## <a name="syntax"></a>Sintaxis  
 *struct-declarator*:  
 *declarator*  
  
 *type-specifier declarator* opt**:** *constant-expression*  
  
 *constant-expression* especifica el ancho del campo en bits. El especificador *type-specifier* para `declarator` debe ser `unsigned int`, **signed int** o `int`, y *constant-expression* debe ser un valor entero no negativo. Si el valor es cero, la declaración no tiene ningún `declarator`. No se permiten matrices de campos de bits, punteros a campos de bits ni funciones que devuelvan campos de bits. El `declarator` opcional asigna el nombre del campo de bits. Los campos de bits solo se pueden declarar como parte de una estructura. No se puede aplicar el operator address-of (**&**) a los componentes de campos de bits.  
  
 No se puede hacer referencia a campos de bits sin nombre y su contenido en tiempo de ejecución es impredecible. Se pueden utilizar como campos "ficticios" para la alineación. Un campo de bits sin nombre cuyo ancho se especifica como 0 garantiza que el almacenamiento para el miembro que hay a continuación en *struct-declaration-list* empieza en un límite `int`.  
  
 Los campos de bits también deben ser suficientemente largos para contener el patrón de bits. Por ejemplo, estas dos instrucciones no son válidas:  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 En este ejemplo se define una matriz bidimensional de estructuras denominada `screen`.  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 La matriz contiene 2000 elementos. Cada elemento es una estructura individual que contiene cuatro miembros de campo de bits: `icon`, `color`, `underline` y `blink`. El tamaño de cada estructura es de dos bytes.  
  
 Los campos de bits tienen la misma semántica que el tipo integer. Esto significa que en las expresiones un campo de bits se utiliza de la misma manera que se usaría una variable del mismo tipo base, independientemente del número de bits que haya en el campo de bits.  
  
 **Específicos de Microsoft**  
  
 Los campos de bits definidos como `int` se tratan como con signo. Una extensión de Microsoft al estándar ANSI C permite tipos `char` y **long** (tanto **signed** como `unsigned`) para los campos de bits. Los campos de bits sin nombre con el tipo base **long**, **short** o `char` (**signed** o `unsigned`) fuerzan la alineación a un límite adecuado para el tipo base.  
  
 Los campos de bits se asignan dentro de un entero del bit menos significativo al bit más significativo. En el código siguiente  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 los bits se organizan de esta forma:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Puesto que la familia de procesadores 8086 almacena el byte bajo de los valores enteros antes que el byte alto, el entero `0x01F2` anterior se almacenaría en la memoria física como `0xF2` seguido de `0x01`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de estructura](../c-language/structure-declarations.md)