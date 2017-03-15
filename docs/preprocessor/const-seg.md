---
title: "const_seg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.const_seg"
  - "const_seg_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_seg (pragma)"
  - "pragma (directivas), const_seg"
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# const_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el segmento en el que las variables [const](../cpp/const-cpp.md) se almacenan en el archivo .obj.  
  
## Sintaxis  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## Comentarios  
 Los términos *segmento* y *sección* son sinónimos en este tema.  
  
 Los archivos OBJ se pueden ver con la aplicación [dumpbin](../build/reference/dumpbin-command-line.md).  El segmento predeterminado en el archivo .obj para las variables `const` es .rdata.  Algunas variables `const`, como las escalares, se alinean automáticamente en la secuencia de código.  El código alineado no aparecerá en .rdata.  
  
 Definir un objeto que requiera una inicialización dinámica en un `const_seg` produce un comportamiento no definido.  
  
 `#pragma const_seg` sin parámetros restablece el segmento en .rdata.  
  
 `push` \(opcional\)  
 Inserta un registro en la pila interna del compilador.  `push` puede tener un parámetro `identifier` y un parámetro `segment-name`.  
  
 `pop` \(opcional\)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 `identifier` \(opcional\)  
 Cuando se usa con `push`, asigna un nombre al registro en la pila interna del compilador.  Cuando se usa con `pop`, extrae los registros de la pila interna hasta que se quita el `identifier`; si no se encuentra el `identifier` en la pila interna, no se extrae nada.  
  
 Usar `identifier` permite sacar varios registros con un solo comando `pop`.  
  
 "`segment-name`" \(opcional\)  
 Nombre de un segmento.  Cuando se usa con `pop`, se extrae la pila y `segment-name` se convierte en el nombre del segmento activo.  
  
 "`segment-class`" \(opcional\)  
 Se incluye por compatibilidad con C\+\+ antes de la versión 2.0.  Se omite.  
  
## Ejemplo  
  
```  
// pragma_directive_const_seg.cpp  
// compile with: /EHsc  
#include <iostream>  
  
const int i = 7;               // inlined, not stored in .rdata  
const char sz1[]= "test1";     // stored in .rdata  
  
#pragma const_seg(".my_data1")  
const char sz2[]= "test2";     // stored in .my_data1  
  
#pragma const_seg(push, stack1, ".my_data2")  
const char sz3[]= "test3";     // stored in .my_data2  
  
#pragma const_seg(pop, stack1) // pop stack1 from stack  
const char sz4[]= "test4";     // stored in .my_data1  
  
int main() {  
    using namespace std;  
   // const data must be referenced to be put in .obj  
   cout << sz1 << endl;  
   cout << sz2 << endl;  
   cout << sz3 << endl;  
   cout << sz4 << endl;  
}  
```  
  
  **test1**  
**test2**  
**test3**  
**test4**   
## Comentarios  
 Para obtener una lista de los nombres que no debe utilizar cuando cree una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 También puede especificar secciones para datos inicializados \([data\_seg](../preprocessor/data-seg.md)\), datos sin inicializar \([bss\_seg](../preprocessor/bss-seg.md)\) y funciones \([code\_seg](../preprocessor/code-seg.md)\).  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)