---
title: "Declaraciones de unión | Microsoft Docs"
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
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
caps.latest.revision: 9
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
ms.openlocfilehash: b68a195bc148dc56f3e5c53cffd91f4d4417ace2
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="union-declarations"></a>Declaraciones de unión
Una "declaración de unión" especifica un conjunto de valores variable y, opcionalmente, una etiqueta que asigna un nombre a la unión. Los valores de variables se denominan "miembros" de la unión y pueden tener diferentes tipos. Las uniones son similares a los "registros de variante" en otros lenguajes.  
  
## <a name="syntax"></a>Sintaxis  
 *struct-or-union-specifier*:  
 *struct-or-union identifier* opt**{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union*:  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 El contenido de la unión se define como  
  
 *struct-declaration*:  
 *specifier-qualifier-list struct-declarator-list* **;**  
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list*:  
 *struct-declarator*  
  
 *struct-declarator-list* **,** *struct-declarator*  
  
 Una variable con tipo **union** almacena uno de los valores definidos por ese tipo. Las mismas reglas rigen las declaraciones de estructura y de unión. Las uniones también pueden tener campos de bits.  
  
 Los miembros de las uniones no pueden tener un tipo incompleto, un tipo `void` o un tipo de función. Por lo tanto, los miembros no pueden ser una instancia de la unión pero pueden ser punteros al tipo de unión que se va a declarar.  
  
 Una declaración de tipo de unión es solo una plantilla. La memoria no se reserva hasta que se declara la variable.  
  
> [!NOTE]
>  Si se declara una unión de dos tipos y se almacena un valor, pero se obtiene acceso a la unión con el otro tipo, los resultados no son confiables. Por ejemplo, se declara una unión de **float** e `int`. Se almacena un valor **float**, pero el programa accede posteriormente al valor como `int`. En esta situación, el valor dependería del almacenamiento interno de los valores **float**. El valor entero no sería confiable.  
  
## <a name="examples"></a>Ejemplos  
 A continuación se incluyen ejemplos de uniones:  
  
```  
union sign   /* A definition and a declaration */  
{  
    int svar;  
    unsigned uvar;  
} number;  
```  
  
 En este ejemplo se define una variable de unión con el tipo `sign` y se declara una variable denominada `number` que tiene dos miembros: `svar`, un entero con signo, y `uvar`, un entero sin signo. Esta declaración permite que el valor actual de `number` se almacene como un valor con signo o sin signo. La etiqueta asociada a este tipo de unión es `sign`.  
  
```  
union               /* Defines a two-dimensional */  
{                   /*  array named screen */  
    struct      
    {   
      unsigned int icon : 8;    
      unsigned color : 4;  
    } window1;  
    int screenval;  
} screen[25][80];  
```  
  
 La matriz `screen` contiene 2.000 elementos. Cada elemento de la matriz es una unión individual con dos miembros: `window1` y `screenval`. El miembro `window1` es una estructura con dos miembros de campos de bits, `icon` y `color`. El miembro `screenval` es `int`. En un momento dado, cada elemento de unión contiene el `int` representado por `screenval` o la estructura representada por `window1`.  
  
 **Específicos de Microsoft**  
  
 Las uniones anidadas se pueden declarar de forma anónima cuando son miembros de otra estructura o unión. Este es un ejemplo de una unión sin nombre:  
  
```  
struct str  
{  
    int a, b;  
    union            / * Unnamed union */  
    {  
      char c[4];  
      long l;  
      float f;  
   };  
   char c_array[10];  
} my_str;  
.  
.  
.  
my_str.l == 0L;  /* A reference to a field in the my_str union */  
```  
  
 Las uniones se suelen anidar dentro de una estructura que incluye un campo que proporciona el tipo de los datos contenidos en la unión en un momento concreto. Este es un ejemplo de una declaración para dicha unión:  
  
```  
struct x  
{  
    int type_tag;  
    union  
    {  
      int x;  
      float y;  
    }  
}  
```  
  
 Vea [Miembros de estructura y unión](../c-language/structure-and-union-members.md) para obtener información sobre cómo se hace referencia a las uniones.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)
