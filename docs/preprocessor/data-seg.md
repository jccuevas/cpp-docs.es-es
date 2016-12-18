---
title: "data_seg | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "data_seg_CPP"
  - "vc-pragma.data_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "data_seg (pragma)"
  - "pragma (directivas), data_seg"
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# data_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el segmento de datos en el que las variables inicializadas se almacenan en el archivo .obj.  
  
## Sintaxis  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## Comentarios  
 Los términos *segmento* y *sección* son sinónimos en este tema.  
  
 Los archivos OBJ se pueden ver con la aplicación [dumpbin](../build/reference/dumpbin-command-line.md).  El segmento predeterminado en el archivo .obj para las variables inicializadas es .data.  Las variables que no están inicializadas se consideran inicializadas en cero y se almacenan en .bss.  
  
 **data\_seg** sin parámetros restablece el segmento en .data.  
  
 **push**\(opcional\)  
 Inserta un registro en la pila interna del compilador.  **push** puede tener *identifier* y *segment\-name*.  
  
 **pop** \(opcional\)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 *identifier* \(opcional\)  
 Cuando se utiliza con **push**, asigna un nombre al registro en la pila interna del compilador.  Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quita el *identifier*; si no se encuentra el *identifier* en la pila interna, no se extrae nada.  
  
 El elemento *identifier* permite que se extraigan varios registros con un solo comando **pop**.  
  
 *"segment\-name"* \(opcional\)  
 Nombre de un segmento*.* Cuando se utiliza con **pop**, se extrae la pila y *segment\-name* se convierte en el nombre de segmento activo.  
  
 *"segment\-class"* \(opcional\)  
 Se incluye por compatibilidad con C\+\+ antes de la versión 2.0.  Se omite.  
  
## Ejemplo  
  
```  
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
  
 Los datos asignados mediante **data\_seg** no conservan información sobre su ubicación.  
  
 Para obtener una lista de los nombres que no debe utilizar cuando cree una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 También puede especificar secciones para las variables const \([const\_seg](../preprocessor/const-seg.md)\), los datos inicializados \([bss\_seg](../preprocessor/bss-seg.md)\) y las funciones \([code\_seg](../preprocessor/code-seg.md)\).  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)