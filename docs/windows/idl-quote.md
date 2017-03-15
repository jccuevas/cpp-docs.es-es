---
title: "idl_quote | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_quote"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_quote attribute"
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# idl_quote
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite utilizar las construcciones IDL que no se admiten en la versión actual de Visual C\+\+ y haga que pasan por el archivo generado .idl.  
  
## Sintaxis  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### Parámetros  
 *text*  
 El nombre de atributo que piensa utilizar el compilador de Visual C\+\+ para recorrer el archivo generado .idl sin devolver un error del compilador.  
  
## Comentarios  
 Si el atributo de **idl\_quote** C\+\+ se utiliza como atributo independiente \(con un punto y coma después del corchete de cierre\), *el texto* se coloca en el archivo combinado .idl como está.  Si **idl\_quote** se utiliza en uno, *el texto* se coloca dentro del bloque de atributos para ese símbolo.  
  
## Ejemplo  
 El código siguiente muestra cómo podría especificar un atributo no admitido \(mediante **en**, se admite que\) y cómo definir y utilizar una construcción undefined .idl:  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 Este código produce MYFLOT y MYDUB y la entrada *de texto* que se va a colocar en el archivo generado .idl.  El parámetro name fuerza *el texto* que se va a colocar antes de que todo lo que hace referencia al *nombre* del archivo generado .idl.  El parámetro *de las dependencias* fuerza las definiciones de lista de dependencias se coloquen antes *de texto* en el archivo generado .idl.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)