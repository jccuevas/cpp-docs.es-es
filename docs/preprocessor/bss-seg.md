---
title: "bss_seg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.bss_seg"
  - "bss_seg_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bss_seg (pragma)"
  - "pragma (directivas), bss_seg"
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# bss_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el segmento en el que las variables sin inicializar se almacenan en el archivo .obj.  
  
## Sintaxis  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## Comentarios  
 Los archivos .obj se pueden ver con la aplicación [dumpbin](../build/reference/dumpbin-command-line.md).  El segmento predeterminado del archivo .obj para los datos sin inicializar es .bss.  En algunos casos, el uso de **bss\_seg** puede reducir los tiempos de carga mediante la agrupación de los datos sin inicializar en una sección.  
  
 **bss\_seg** sin parámetros restablece el segmento a .bss.  
  
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
  
 También puede especificar secciones para los datos inicializados \([data\_seg](../preprocessor/data-seg.md)\), las funciones \([code\_seg](../preprocessor/code-seg.md)\) y las variables const \([const\_seg](../preprocessor/const-seg.md)\).  
  
 Los datos asignados mediante el uso de la directiva pragma **bss\_seg** no conservan información sobre su ubicación.  
  
 Para obtener una lista de los nombres que no debe utilizar cuando cree una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)