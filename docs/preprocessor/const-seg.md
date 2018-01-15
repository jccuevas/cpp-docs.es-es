---
title: const_seg | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49d145bc80b524176b381b2b5938c9707e8c1b19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="constseg"></a>const_seg
Especifica el segmento donde [const](../cpp/const-cpp.md) variables se almacenan en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Comentarios  
 El significado de los términos de *segmento* y *sección* son sinónimos en este tema.  
  
 Archivos OBJ se pueden ver con el [dumpbin](../build/reference/dumpbin-command-line.md) aplicación. El segmento predeterminado en el archivo .obj para las variables `const` es .rdata. Algunas variables `const`, como las escalares, se alinean automáticamente en la secuencia de código. El código alineado no aparecerá en .rdata.  
  
 Definir un objeto que requiera una inicialización dinámica en un `const_seg` produce un comportamiento no definido.  
  
 `#pragma const_seg` sin parámetros restablece el segmento en .rdata.  
  
 `push` (opcional)  
 Inserta un registro en la pila interna del compilador. `push` puede tener un parámetro `identifier` y un parámetro `segment-name`.  
  
 `pop` (opcional)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 `identifier` (opcional)  
 Cuando se usa con `push`, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con `pop`, extrae los registros de la pila interna hasta que se quita el `identifier`; si no se encuentra el `identifier` en la pila interna, no se extrae nada.  
  
 Usar `identifier` permite sacar varios registros con un solo comando `pop`.  
  
 "`segment-name`" (opcional)  
 Nombre de un segmento. Cuando se usa con `pop`, se extrae la pila y `segment-name` se convierte en el nombre del segmento activo.  
  
 "`segment-class`" (opcional)  
 Se incluye por compatibilidad con C++ antes de la versión 2.0. Se omite.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
test1  
test2  
test3  
test4  
```  
  
## <a name="comments"></a>Comentarios  
 Vea [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de nombres que no se debe utilizar cuando cree una sección.  
  
 También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos inicializados ([bss_seg](../preprocessor/bss-seg.md)) y funciones ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)