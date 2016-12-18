---
title: "code_seg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "code_seg_CPP"
  - "vc-pragma.code_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "code_seg (pragma)"
  - "pragma (directivas), code_seg"
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# code_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el segmento de texto donde se almacenan las funciones en el archivo .obj.  
  
## Sintaxis  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## Comentarios  
 La directiva pragma `code_seg` no controla la posición del código objeto generado para las plantillas con instancias ni el código generado implícitamente por compilador, por ejemplo, funciones miembro especiales.  Se recomienda usar el atributo [\_\_declspec\(code\_seg\(...\)\)](../cpp/code-seg-declspec.md) en su lugar ya que ofrece control sobre la posición de todo el código objeto.  Esto incluye el código generado por el compilador.  
  
 Un *segmento* de un archivo .obj es un bloque de datos con nombre que se carga en memoria como una unidad.  Un *segmento de texto* es un segmento que contiene código ejecutable.  En este caso, se usan indistintamente los términos *segmento* y *sección*.  
  
 La directiva pragma `code_seg` indica al compilador que coloque todo el código objeto posterior de la unidad de traducción en un segmento de texto denominado `segment-name`.  De forma predeterminada, el segmento de texto usado para las funciones de un archivo .obj se denomina .text.  
  
 Una directiva pragma `code_seg` sin parámetros restablece el nombre del segmento de texto para el código objeto posterior a .text.  
  
 **Push** \(opcional\)  
 Inserta un registro en la pila interna del compilador.  **push** puede tener un parámetro `identifier` y un parámetro `segment-name`.  
  
 **pop** \(opcional\)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 `identifier` \(opcional\)  
 Cuando se usa con **push**, asigna un nombre al registro en la pila interna del compilador.  Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quita el `identifier`; si no se encuentra el `identifier` en la pila interna, no se extrae nada.  
  
 `identifier` permite sacar varios registros con un solo comando **pop**.  
  
 "`segment-name`" \(opcional\)  
 Nombre de un segmento.  Cuando se usa con **pop**, se extrae la pila y `segment-name` se convierte en el nombre del segmento de texto activo.  
  
 "`segment-class`" \(opcional\)  
 Se omite, pero se incluye por compatibilidad con las versiones de C\+\+ anteriores a la versión 2.0.  
  
 Se puede usar la aplicación [DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) para ver archivos .obj.  Las versiones de DUMPBIN para cada arquitectura de destino admitida se incluyen con [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## Ejemplo  
 En este ejemplo se muestra cómo usar la directiva pragma `code_seg` para controlar dónde se coloca el código objeto:  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 Para obtener una lista de los nombres que no se deben usar para crear una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 También puede especificar secciones para datos inicializados \([data\_seg](../preprocessor/data-seg.md)\), datos sin inicializar \([bss\_seg](../preprocessor/bss-seg.md)\) y variables const \([const\_seg](../preprocessor/const-seg.md)\).  
  
## Vea también  
 [code\_seg \(\_\_declspec\)](../cpp/code-seg-declspec.md)   
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)