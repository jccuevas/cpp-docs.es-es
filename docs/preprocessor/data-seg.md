---
title: data_seg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1be97919f0f5b55d6e63eca8e59eb15e8ef9dff
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538504"
---
# <a name="dataseg"></a>data_seg
Especifica el segmento de datos en el que las variables inicializadas se almacenan en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Comentarios 

El significado de los términos *segmento* y *sección* son intercambiables en este tema.  
  
Archivos OBJ pueden verse con el [dumpbin](../build/reference/dumpbin-command-line.md) aplicación. El segmento predeterminado en el archivo .obj para las variables inicializadas es .data. Las variables que no están inicializadas se consideran inicializadas en cero y se almacenan en .bss.  
  
**data_seg** sin parámetros restablece el segmento en. Data.  
  
*inserción* (opcional)  
Inserta un registro en la pila interna del compilador. Un *inserción* puede tener un *identificador* y *nombre de segmento*.  
  
*POP* (opcional)  
Quita un registro de la parte superior de la pila interna del compilador.  
  
*identificador* (opcional)  
Cuando se usa con *inserción*, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con *pop*, extrae los registros de la pila interna hasta *identificador* se quita; si *identificador* no se encuentra en la pila interna, no se extrae nada.  
  
*identificador* permite varios registros que se saque con una sola *pop* comando.  
  
*"segment-name"*(opcional)  
Nombre de un segmento. Cuando se usa con *pop*, se extrae la pila y *nombre de segmento* se convierte en el nombre del segmento activo.  
  
*"clase de segmento"* (opcional)  
Se incluye por compatibilidad con C++ antes de la versión 2.0. Se omite.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
Los datos asignados mediante **data_seg** no conservan información sobre su ubicación.  
  
Consulte [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de los nombres no debe utilizar cuando cree una sección.  
  
También puede especificar secciones para las variables const ([const_seg](../preprocessor/const-seg.md)), datos sin inicializar ([bss_seg](../preprocessor/bss-seg.md)) y funciones ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)