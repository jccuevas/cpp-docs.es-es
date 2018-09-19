---
title: const_seg | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db73d212a11fe096c07a7e14d033c21e6b61311c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705216"
---
# <a name="constseg"></a>const_seg
Especifica el segmento donde [const](../cpp/const-cpp.md) las variables se almacenan en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
### <a name="parameters"></a>Parámetros

**push**<br/>
(Opcional) Inserta un registro en la pila interna del compilador. Un **inserción** puede tener un *identificador* y *nombre de segmento*.  
  
**pop**<br/>
(Opcional) Quita un registro de la parte superior de la pila interna del compilador.  
  
*identifier*<br/>
(Opcional) Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta *identificador* se quita; si *identificador* no se encuentra en la pila interna, no se extrae nada.  
  
Uso de *identificador* permite varios registros que se saque con una sola **pop** comando.  
  
"*nombre de segmento*"<br/>  
(Opcional) El nombre de un segmento. Cuando se usa con **pop**, se extrae la pila y *nombre de segmento* se convierte en el nombre del segmento activo.  
  
"*clase de segmento*"<br/>
(Opcional) Se incluye por compatibilidad con C++ antes de la versión 2.0. Se omite.  
  
## <a name="remarks"></a>Comentarios

El significado de los términos *segmento* y *sección* son intercambiables en este tema.  
  
Archivos OBJ pueden verse con el [dumpbin](../build/reference/dumpbin-command-line.md) aplicación. El segmento predeterminado en el archivo .obj para las variables `const` es .rdata. Algunas variables `const`, como las escalares, se alinean automáticamente en la secuencia de código. El código alineado no aparecerá en .rdata.  
  
Definir un objeto que requiera una inicialización dinámica en un `const_seg` produce un comportamiento no definido.  
  
`#pragma const_seg` sin parámetros restablece el segmento en .rdata.

## <a name="example"></a>Ejemplo  
  
```cpp  
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
 
Consulte [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de los nombres no debe utilizar cuando cree una sección.  
  
También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos sin inicializar ([bss_seg](../preprocessor/bss-seg.md)) y funciones ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)