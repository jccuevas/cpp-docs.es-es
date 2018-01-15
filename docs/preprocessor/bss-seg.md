---
title: bss_seg | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dd1e24127129ef833cfd4906085eabbf1e5c380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bssseg"></a>bss_seg
Especifica el segmento en el que las variables sin inicializar se almacenan en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Archivos obj se pueden ver con el [dumpbin](../build/reference/dumpbin-command-line.md) aplicación. El segmento predeterminado del archivo .obj para los datos sin inicializar es .bss. En algunos casos el uso de **bss_seg** puede acelerar tiempos empleados para cargar mediante la agrupación de datos sin inicializar en una sección.  
  
 **bss_seg** sin parámetros restablece el segmento en BSS.  
  
 **inserción**(opcional)  
 Inserta un registro en la pila interna del compilador. A **inserción** puede tener un *identificador* y *nombre de segmento*.  
  
 **confirmación** (opcional)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 *identificador* (opcional)  
 Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae registros de la pila interna hasta que *identificador* se quita; si *identificador* no se encuentra en la pila interna, se extrae nada.  
  
 *identificador* permite varios registros sacar con una sola **pop** comando.  
  
 *"segment-name"*(opcional)  
 Nombre de un segmento. Cuando se usa con **pop**, se extrae la pila y *nombre de segmento* se convierte en el nombre del segmento activo.  
  
 *"clase de segmento"* (opcional)  
 Se incluye por compatibilidad con C++ antes de la versión 2.0. Se omite.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
 Datos asignados mediante el **bss_seg** pragma no conserva toda la información sobre su ubicación.  
  
 Vea [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de nombres que no se debe utilizar cuando cree una sección.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)