---
title: sección | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs:
- C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7601913b3940de8e6ade2c76100f4d773281db7
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538704"
---
# <a name="section"></a>section
Crea una sección en un archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma section( "section-name" [, attributes] )  
```  
  
## <a name="remarks"></a>Comentarios  
 
El significado de los términos *segmento* y *sección* son intercambiables en este tema.  
  
Cuando se define una sección, sigue siendo válida para el resto de la compilación. Sin embargo, debe usar [__declspec (allocate)](../cpp/allocate.md) o nada se colocarán en la sección.  
  
*nombre de sección* es un parámetro obligatorio que será el nombre de la sección. El nombre no debe estar en conflicto con ningún nombre de sección estándar. Consulte [/SECTION](../build/reference/section-specify-section-attributes.md) para obtener una lista de los nombres no debe utilizar cuando cree una sección.  
  
*atributos* es un parámetro opcional que consta de uno o varios atributos de separados por comas que se desean asignar a la sección. Posible *atributos* son:  
  
**read**  
Permite operaciones de lectura en los datos.  
  
**write**  
Permite operaciones de escritura en los datos.  
  
**Ejecutar**  
Permite que el código se ejecute.  
  
**Compartido**  
Comparte la sección entre todos los procesos que cargan la imagen.  
  
**nopage**  
Marca la sección como no paginable; útil para controladores de dispositivo de Win32.  
  
**NoCache**  
Marca la sección como no almacenable en caché; útil para controladores de dispositivo de Win32.  
  
**discard**  
Marca la sección como no descartable; útil para controladores de dispositivo de Win32.  
  
**remove**  
Marca la sección como no residente en memoria; controladores de dispositivos virtuales (V*x*d.) solo.  
  
Si no especifica atributos, la sección tendrá atributos de lectura y escritura.  
  
## <a name="example"></a>Ejemplo  
 
En el ejemplo siguiente, la primera instrucción identifica la sección y sus atributos. El entero `j` no se coloca en `mysec` porque no se declaró con `__declspec(allocate)`; `j` va a la sección de datos. El entero `i` sí va a `mysec` como resultado de su atributo de clase de almacenamiento `__declspec(allocate)`.  
  
```cpp  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)