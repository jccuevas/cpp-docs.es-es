---
title: code_seg | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs: C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91834205187ecfa3c56c04aaac9cd0a2d25b49fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="codeseg"></a>code_seg
Especifica el segmento de texto donde se almacenan las funciones en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Comentarios  
 La directiva pragma `code_seg` no controla la posición del código objeto generado para las plantillas con instancias ni el código generado implícitamente por compilador, por ejemplo, funciones miembro especiales. Se recomienda que realice la [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) atributo en su lugar, ya que ofrece control sobre la posición de todo el código objeto. Esto incluye el código generado por el compilador.  
  
 A *segmento* en un .obj archivo es un bloque de datos que se cargan en memoria como una unidad con nombre. A *segmento de texto* es un segmento que contiene código ejecutable. En este artículo, los términos *segmento* y *sección* se usan indistintamente.  
  
 La directiva pragma `code_seg` indica al compilador que coloque todo el código objeto posterior de la unidad de traducción en un segmento de texto denominado `segment-name`. De forma predeterminada, el segmento de texto usado para las funciones de un archivo .obj se denomina .text.  
  
 Una directiva pragma `code_seg` sin parámetros restablece el nombre del segmento de texto para el código objeto posterior a .text.  
  
 **Insertar** (opcional)  
 Inserta un registro en la pila interna del compilador. A **inserción** puede tener un `identifier` y `segment-name`.  
  
 **confirmación** (opcional)  
 Quita un registro de la parte superior de la pila interna del compilador.  
  
 `identifier` (opcional)  
 Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae registros de la pila interna hasta que `identifier` se quita; si `identifier` no se encuentra en la pila interna, se extrae nada.  
  
 `identifier`permite sacar con solo uno de varios registros **pop** comando.  
  
 "`segment-name`" (opcional)  
 Nombre de un segmento. Cuando se usa con **pop**, se extrae la pila y `segment-name` se convierte en el nombre del segmento de texto activo.  
  
 "`segment-class`" (opcional)  
 Se omite, pero se incluye por compatibilidad con las versiones de C++ anteriores a la versión 2.0.  
  
 Puede usar el [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) aplicación para ver los archivos .obj. Las versiones de DUMPBIN para cada arquitectura de destino admitida se incluyen con [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Ejemplo  
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
  
 Para obtener una lista de nombres que no debe usarse para crear una sección, vea [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 También puede especificar secciones para datos inicializados ([data_seg](../preprocessor/data-seg.md)), datos inicializados ([bss_seg](../preprocessor/bss-seg.md)) y las variables const ([const_seg](../preprocessor/const-seg.md)).  
  
## <a name="see-also"></a>Vea también  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)