---
title: "Declaraciones typedef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "declaraciones, typedef"
  - "declaraciones typedef"
  - "tipos [C], declaraciones"
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Declaraciones typedef
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una declaración typedef es una declaración con typedef como clase de almacenamiento.  El declarador se convierte en un nuevo tipo.  Puede utilizar declaraciones typedef para construir nombres más cortos o más significativos para tipos ya definidos por C o para tipos que haya declarado.  Los nombres de typedef permiten encapsular detalles de la implementación que pueden cambiar.  
  
 Una declaración typedef se interpreta igual que una declaración de variable o de función, pero el identificador, en lugar de suponer el tipo especificado por la declaración, se convierte en un sinónimo del tipo.  
  
## Sintaxis  
 `declaration`:  
 *declaration\-specifiers init\-declarator\-list*  opt **;**  
  
 *declaration\-specifiers*:  
 *storage\-class\-specifier declaration\-specifiers*  opt  
  
 *type\-specifier declaration\-specifiers*  opt  
  
 *type\-qualifier declaration\-specifiers*  opt  
  
 *storage\-class\-specifier*:  
 `typedef`  
  
 *type\-specifier*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 *typedef\-name*:  
 *identifier*  
  
 Observe que una declaración typedef no crea tipos.  Crea los sinónimos de tipos existentes o nombres para tipos que se podrían especificar de otras maneras.  Cuando se usa un nombre typedef como especificador de tipo, puede combinarse con determinados especificadores de tipo, pero no con otros.  Los modificadores aceptables son **const** y `volatile`.  
  
 Los nombres de typedef comparten el espacio de nombres con identificadores normales \(vea [Espacios de nombres](../c-language/name-spaces.md) para obtener más información\).  Por tanto, un programa puede tener un nombre de typedef y un identificador de ámbito local con el mismo nombre.  Por ejemplo:  
  
```  
typedef char FlagType;  
  
int main()  
{  
}  
  
int myproc( int )  
{  
    int FlagType;  
}  
```  
  
 Al declarar un identificador de ámbito local con el mismo nombre que un typedef, o al declarar un miembro de una estructura o una unión en el mismo ámbito o en un ámbito interno, se debe indicar el especificador de tipo.  Este ejemplo muestra esta restricción:  
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Para reutilizar el nombre `FlagType` para un identificador, un miembro de una estructura o un miembro de una unión, se debe proporcionar el tipo:  
  
```  
const int FlagType;  /* Type specifier required */  
```  
  
 No basta con decir  
  
```  
const FlagType;      /* Incomplete specification */  
```  
  
 porque se considera que `FlagType` forma parte del tipo, no un identificador que se va a volver a declarar.  Esta declaración se considera no válida como  
  
```  
int;  /* Illegal declaration */  
```  
  
 Es posible declarar cualquier tipo con typedef, incluidos los tipos de puntero, función y matriz.  Se puede declarar un nombre de typedef para un puntero a un tipo de estructura o de unión antes de definir el tipo de estructura o de unión, siempre y cuando la definición tenga la misma visibilidad que la declaración.  
  
 Los nombres typedef se pueden usar para mejorar la legibilidad del código.  Las tres siguientes declaraciones de `signal` especifican exactamente el mismo tipo, la primera sin hacer uso de ningún nombre typedef.  
  
```  
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */  
  
void ( *signal( int, void (*) (int)) ) ( int );  
fv *signal( int, fv * );   /* Uses typedef type */  
pfv signal( int, pfv );    /* Uses typedef type */  
```  
  
## Ejemplos  
 En los ejemplos siguientes se muestran declaraciones typedef:  
  
```  
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */  
```  
  
 Observe que `WHOLE` se podría usar ahora en una declaración de variable tal como `WHOLE i;` o `const WHOLE i;`.  Sin embargo, la declaración `long WHOLE i;` no sería válida.  
  
```  
typedef struct club   
{  
    char name[30];  
    int size, year;  
} GROUP;  
```  
  
 Esta instrucción declara `GROUP` como un tipo de estructura con tres miembros.  Dado que también se especifica una etiqueta de estructura, `club`, tanto el nombre typedef \(`GROUP`\) como la etiqueta de estructura se pueden usar en declaraciones.  Se debe usar la palabra clave struct con la etiqueta y no se puede usar la palabra clave struct con el nombre typedef.  
  
```  
typedef GROUP *PG; /* Uses the previous typedef name   
                      to declare a pointer            */  
```  
  
 El tipo `PG` se declara como un puntero al tipo `GROUP`, que a su vez se define como un tipo de estructura.  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Este ejemplo proporciona el tipo `DRAWF` para una función que no devuelve ningún valor y que acepta dos argumentos int.  Esto significa, por ejemplo, que la declaración  
  
```  
DRAWF box;   
```  
  
 es equivalente a la declaración  
  
```  
void box( int, int );  
```  
  
## Vea también  
 [\(NOTINBUILD\)typedef Specifier](http://msdn.microsoft.com/es-es/cc96cf26-ba93-4179-951e-695d1f5fdcf1)