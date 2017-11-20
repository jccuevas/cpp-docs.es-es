---
title: "Información general sobre las declaraciones | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f0ac465ec20d0893add63d8b5791b9445b17f8fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-declarations"></a>Información general sobre las declaraciones
Una "declaración" especifica la interpretación y los atributos de un conjunto de identificadores. Una declaración que también reserva almacenamiento para el objeto o la función especificada por el identificador se denomina "definición". Las declaraciones de C para variables, funciones y tipos tienen esta sintaxis:  
  
## <a name="syntax"></a>Sintaxis  
 `declaration`:  
 *declaration-specifiers* *attribute-seq*opt*init-declarator-list*opt**;**  
  
 /\* *attribute-seq*opt es específico de Microsoft */  
  
 *declaration-specifiers*:  
 *storage-class-specifier declaration-specifiers*opt  
  
 *type-specifier declaration-specifiers*opt  
  
 *type-qualifier declaration-specifiers*opt  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init-declarator-list* , *init-declarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *declarator*  **=**  *initializer*  
  
> [!NOTE]
>  Esta sintaxis para `declaration` no se repite en las próximas secciones. La sintaxis de las próximas secciones suele empezar con el `declarator` no terminal.  
  
 Las declaraciones en *init-declarator-list* contienen los identificadores indicados; *init* es una abreviatura de inicializador. *init-declarator-list* es una secuencia separada por comas de declaradores, cada uno de los cuales puede tener información de tipos adicional, un inicializador o ambas cosas. El `declarator` contiene los identificadores, si hay alguno, que se van a declarar. Los especificadores *declaration-specifiers* no terminales constan de una secuencia de especificadores de tipo y de clase de almacenamiento que indican la vinculación, la duración del almacenamiento y al menos parte del tipo de las entidades que los declaradores representan. Por tanto, las declaraciones se componen de una combinación de especificadores de clase de almacenamiento, especificadores de tipo, calificadores de tipo, declaradores e inicializadores.  
  
 Las declaraciones pueden contener uno o varios de los atributos opcionales enumerados en la secuencia de atributos *attribute-seq*; *seq* es una abreviatura de secuencia. Estos atributos específicos de Microsoft realizan diversas funciones, que se describen con más detalle a lo largo de este documento.  
  
 En el formato general de una declaración de variable, el especificador *type-specifier* proporciona el tipo de datos de la variable. El especificador *type-specifier* puede ser compuesto, como cuando el tipo se modifica mediante **const** o `volatile`. El `declarator` proporciona el nombre de la variable, modificado posiblemente para declarar un tipo de matriz o de puntero. Por ejemplo,  
  
```  
int const *fp;  
```  
  
 declara una variable con nombre `fp` como puntero a un valor `int` no modificable (**const**). Se pueden definir varias variables en una declaración si se utilizan varios declaradores separados por comas.  
  
 Una declaración debe tener al menos un declarador, o su especificador de tipo debe declarar una etiqueta de estructura, una etiqueta de unión o miembros de una enumeración. Los declaradores proporcionan toda la información restante sobre un identificador. Un declarador es un identificador que se puede modificar con corchetes (**[ ]**), asteriscos (**\***) o paréntesis ( **( )** ) para declarar una matriz, un puntero o un tipo de función, respectivamente. Cuando se declaran variables simples (como elementos de carácter, entero y punto flotante), o estructuras y uniones de variables simples, `declarator` es simplemente un identificador. Para más información sobre los declaradores, vea [Declaradores y declaraciones de variable](../c-language/declarators-and-variable-declarations.md).  
  
 Todas las definiciones son declaraciones de forma implícita, pero no todas las declaraciones son definiciones. Por ejemplo, las declaraciones de variable que comienzan con el especificador de clase de almacenamiento `extern` son de "referencia", no de "definición". Si se va a hacer referencia a una variable externa antes de definirse, o si se ha definido en otro archivo de código fuente distinto del archivo donde se utiliza, es necesaria una declaración `extern`. El almacenamiento no se asigna mediante declaraciones de "referencia" ni se pueden inicializar variables en las declaraciones.  
  
 Se necesita una clase de almacenamiento o un tipo (o ambos) en las declaraciones de variable. A excepción de `__declspec`, solo se permite un especificador de clase de almacenamiento en una declaración y no se permiten todos los especificadores de clase de almacenamiento en todos los contextos. La clase de almacenamiento `__declspec` se permite con otros especificadores de clase de almacenamiento, y se permite más de una vez. El especificador de clase de almacenamiento de una declaración afecta a cómo se almacena e inicializa el elemento declarado, y a qué partes de un programa pueden hacer referencia al elemento.  
  
 Entre los elementos especificadores de clase de almacenamiento *storage-class-specifier* terminales definidos en C se incluyen **auto**, `extern`, **register**, **static** y `typedef`. Además, Microsoft C incluye el elemento *storage-class-specifier* terminal `__declspec`. Todos los elementos *storage-class-specifier* terminales excepto `typedef` y `__declspec` se describen en [Clases de almacenamiento](../c-language/c-storage-classes.md). Vea [Declaraciones typedef](../c-language/typedef-declarations.md) para obtener información sobre `typedef`. Vea [Atributos extendidos de clase de almacenamiento](../c-language/c-extended-storage-class-attributes.md) para obtener información sobre `__declspec`.  
  
 La ubicación de la declaración dentro del programa fuente y la presencia o ausencia de otras declaraciones de la variable son factores importantes a la hora de determinar la duración de las variables. Puede haber varias redeclaraciones pero solo una definición. Sin embargo, una definición puede aparecer en más de una unidad de traducción. En el caso de objetos con vinculación interna, esta regla se aplica por separado a cada unidad de traducción, ya que los objetos vinculados internamente son únicos en una unidad de traducción. En los objetos con vinculación externa, esta regla se aplica a todo el programa. Vea [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md) para obtener más información sobre la visibilidad.  
  
 Los especificadores de tipo proporcionan cierta información sobre los tipos de datos de los identificadores. El especificador de tipo predeterminado es `int`. Para obtener más información, vea [Especificadores de tipo](../c-language/c-type-specifiers.md). Los especificadores de tipo también pueden definir etiquetas de tipo, nombres de componentes de estructura y unión, y constantes de enumeración. Para más información, vea [Declaraciones de enumeración](../c-language/c-enumeration-declarations.md), [Declaraciones de estructura](../c-language/structure-declarations.md) y [Declaraciones de unión](../c-language/union-declarations.md).  
  
 Hay dos *type-qualifier* terminales: **const** y `volatile`. Estos calificadores especifican propiedades adicionales de los tipos que son pertinentes solo cuando se obtiene acceso a objetos de ese tipo mediante valores L. Para más información sobre **const** y `volatile`, vea [Calificadores de tipo](../c-language/type-qualifiers.md). Para obtener una definición de los valores L, vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md).  
  
## <a name="see-also"></a>Vea también  
 [Resumen de la sintaxis de lenguaje C](../c-language/c-language-syntax-summary.md)   
 [Declaraciones y tipos](../c-language/declarations-and-types.md)   
 [Resumen de declaraciones](../c-language/summary-of-declarations.md)