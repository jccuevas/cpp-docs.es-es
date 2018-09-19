---
title: bss_seg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c3a80e50bd0b012773a5e5a197674965f73b526
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711163"
---
# <a name="bssseg"></a>bss_seg
Especifica el segmento en el que las variables sin inicializar se almacenan en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Comentarios  

Archivos obj pueden verse con el [dumpbin](../build/reference/dumpbin-command-line.md) aplicación. El segmento predeterminado del archivo .obj para los datos sin inicializar es .bss. En algunos casos de uso de **bss_seg** puede acelerar tiempos de carga mediante la agrupación de datos sin inicializar en una sección.  
  
**bss_seg** sin parámetros restablece el segmento a. BSS.  
  
**push**<br/>
(Opcional) Inserta un registro en la pila interna del compilador. Un *pu*sh * puede tener un *identificador* y *nombre de segmento*.  
  
**pop**<br/>
(Opcional) Quita un registro de la parte superior de la pila interna del compilador.  
  
*identifier*<br/>
(Opcional) Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta *identificador* se quita; si *identificador* no se encuentra en la pila interna, no se extrae nada.  
  
*identificador* permite varios registros que se saque con una sola **pop** comando.  
  
*"segment-name"*<br/>
(Opcional) El nombre de un segmento. Cuando se usa con **pop**, se extrae la pila y *nombre de segmento* se convierte en el nombre del segmento activo.  
  
*"segmento-class"*<br/>
(Opcional) Se incluye por compatibilidad con C++ antes de la versión 2.0. Se omite.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), las funciones ([code_seg](../preprocessor/code-seg.md)) y las variables const ([const_seg](../preprocessor/const-seg.md)).  
  
Los datos asignados mediante el **bss_seg** pragma no conservan información sobre su ubicación.  
  
Consulte [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de los nombres no debe utilizar cuando cree una sección.  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)