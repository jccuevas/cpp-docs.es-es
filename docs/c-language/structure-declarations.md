---
title: Declaraciones de estructura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7d305b2bc74455abd6fdbcfb29ed7ef4103bf19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="structure-declarations"></a>Declaraciones de estructura
Una "declaración de estructura" designa un tipo y especifica una secuencia de valores variables (denominados “miembros” o “campos” de la estructura) que pueden tener diferentes tipos. Un identificador opcional, denominado “etiqueta”, proporciona el nombre del tipo de estructura y se puede usar en referencias posteriores al tipo de estructura. Una variable de este tipo de estructura contiene la secuencia completa definida por el tipo. Las estructuras de C son similares a los tipos denominados "registros" en otros lenguajes.  
  
## <a name="syntax"></a>Sintaxis  
 *struct-or-union-specifier*:  
 *struct-or-union identifier* opt **{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union*:  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 El contenido de la estructura se define como  
  
 *struct-declaration*:  
 *specifier-qualifier-list struct-declarator-list* **;**  
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list*:  
 *struct-declarator*  
  
 *struct-declarator-list* **,** *struct-declarator*  
  
 *struct-declarator*:  
 `declarator`  
  
 La declaración de un tipo de estructura no reserva espacio para una estructura. Es solo una plantilla para declaraciones posteriores de variables de estructura.  
  
 Se puede usar un elemento *identifier* (etiqueta) definido previamente para hacer referencia a un tipo de estructura definido en otra parte. En este caso, *struct-declaration-list* no se puede repetir mientras la definición esté visible. Las declaraciones de punteros a estructuras y los typedef de tipos de estructuras pueden usar la etiqueta de estructura antes de que se defina el tipo de estructura. Sin embargo, la definición de estructura se debe encontrar antes que cualquier uso real del tamaño de los campos. Esta es una definición incompleta del tipo y la etiqueta de tipo. Para que esta definición esté completa, una definición de tipo debe aparecer más adelante en el mismo ámbito.  
  
 El elemento *struct-declaration-list* especifica los tipos y los nombres de los miembros de la estructura. Un argumento *struct-declaration-list* contiene una o varias declaraciones de variables o campos de bits.  
  
 Cada variable declarada en *struct-declaration-list* se define como un miembro del tipo de estructura. Las declaraciones de variable dentro de *struct-declaration-list* tienen el mismo formato que otras declaraciones de variable descritas en esta sección, con la salvedad de que no pueden contener inicializadores ni especificadores de clase de almacenamiento. Los miembros de la estructura pueden tener cualquier tipo de variable excepto el tipo `void`, un tipo incompleto o un tipo de función.  
  
 Un miembro no se puede declarar para que tenga el tipo de la estructura en la que aparece. Sin embargo, un miembro puede declararse como un puntero al tipo de estructura en la que aparece siempre y cuando el tipo de estructura tenga una etiqueta. Esto permite crear listas de estructuras vinculadas.  
  
 Las estructuras siguen la misma definición de ámbito que otros identificadores. Los identificadores de estructura deben ser distintos de otras etiquetas de estructura, unión y enumeración con la misma visibilidad.  
  
 Cada *struct-declaration* de un elemento *struct-declaration-list* debe ser única dentro de la lista. En cambio, los nombres de identificador de un elemento *struct-declaration-list* no tienen que ser distintos de los nombres de variable normales o de los identificadores en otras listas de declaraciones de estructura.  
  
 A las estructuras anidadas también se puede acceder como si se hubieran declarado en el nivel de ámbito de archivo. Por ejemplo, dada esta declaración:  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 estas declaraciones son válidas:  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>Ejemplos  
 En estos ejemplos se muestran declaraciones de estructura:  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 La estructura `employee` tiene tres miembros: `name`, `id` y `class`. El miembro `name` es una matriz de 20 elementos, e `id` y `class` son miembros simples con `int` y el tipo **long**, respectivamente. El identificador `employee` es el identificador de la estructura.  
  
```  
struct employee student, faculty, staff;  
```  
  
 En este ejemplo se definen tres variables de estructura: `student`, `faculty` y `staff`. Cada estructura tiene la misma lista de tres miembros. Los miembros se declaran para que tengan el tipo de estructura `employee`, definido en el ejemplo anterior.  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 La estructura `complex` tiene dos miembros con el tipo **float**, `x` e `y`. El tipo de estructura no tiene ninguna etiqueta y, por tanto, es un tipo sin nombre o anónimo.  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 Los dos primeros miembros de la estructura son una variable `char` y un puntero a un valor **float**. El tercer miembro, `next`, se declara como un puntero al tipo de estructura que se va a definir (`sample`).  
  
 Las estructuras anónimas pueden resultar útiles cuando no se requiere una etiqueta con nombre. Esto ocurre cuando una declaración define todas las instancias de la estructura. Por ejemplo:  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 Las estructuras incrustadas suelen ser anónimas.  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Específicos de Microsoft**  
  
 El compilador permite una matriz sin tamaño o de tamaño cero como el último miembro de una estructura. Esto puede ser útil si el tamaño de una matriz constante es diferente según en la situación en la que se use. La declaración de este tipo de estructura tiene el siguiente aspecto:  
  
 `struct` *identifier***{** *set-of-declarations* *type array-name***[ ];};**  
  
 Las matrices sin tamaño solo pueden aparecer como el último miembro de una estructura. Las estructuras que contienen declaraciones de matriz sin tamaño se pueden anidar dentro de otras estructuras siempre y cuando no se declaren como miembros en ninguna de las estructuras contenedoras. Las matrices de estas estructuras no se permiten. El operador `sizeof`, cuando se aplica a una variable de este tipo o al propio tipo, asume que el tamaño de la matriz es 0.  
  
 Las declaraciones de estructura también se pueden especificar sin un declarador cuando son miembros de otra estructura o unión. Los nombres de campo se promueven a la estructura contenedora. Por ejemplo, una estructura sin nombre tiene el siguiente aspecto:  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 Consulte [Miembros de estructura y unión](../c-language/structure-and-union-members.md) para obtener información sobre las referencias de estructura.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)