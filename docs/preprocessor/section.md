---
title: "section | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "section_CPP"
  - "vc-pragma.section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pragma (directivas), section"
  - "section (pragma)"
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# section
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una sección en un archivo .obj.  
  
## Sintaxis  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## Comentarios  
 Los términos *segmento* y *sección* son sinónimos en este tema.  
  
 Cuando se define una sección, sigue siendo válida para el resto de la compilación.  Sin embargo, debe utilizar [\_\_declspec \(allocate\)](../cpp/allocate.md) o no se colocará nada en la sección.  
  
 *section\-name* es un parámetro obligatorio que será el nombre de la sección.  El nombre no debe estar en conflicto con ningún nombre de sección estándar.  Para obtener una lista de los nombres que no debe utilizar cuando cree una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 `attributes` es un parámetro opcional que consta de uno o más atributos separados por comas y que se desea asignar a la sección.  Posibles `attributes` son:  
  
 **lectura**  
 Permite operaciones de lectura en los datos.  
  
 **escritura**  
 Permite operaciones de escritura en los datos.  
  
 **execute**  
 Permite que el código se ejecute.  
  
 **compartido**  
 Comparte la sección entre todos los procesos que cargan la imagen.  
  
 **nopage**  
 Marca la sección como no paginable; útil para controladores de dispositivo de Win32.  
  
 **nocache**  
 Marca la sección como no almacenable en caché; útil para controladores de dispositivo de Win32.  
  
 **discard**  
 Marca la sección como no descartable; útil para controladores de dispositivo de Win32.  
  
 **remove**  
 Marca la sección como no residente en memoria; solo controladores de dispositivo virtual \(V*x*D\) solo.  
  
 Si no especifica atributos, la sección tendrá atributos de lectura y escritura.  
  
## Ejemplo  
 En el ejemplo siguiente, la primera instrucción identifica la sección y sus atributos.  El entero `j` no se coloca en `mysec` porque no se declaró con `__declspec(allocate)`; `j` va a la sección de datos.  El entero `i` sí va a `mysec` como resultado de su atributo de clase de almacenamiento `__declspec(allocate)`.  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)