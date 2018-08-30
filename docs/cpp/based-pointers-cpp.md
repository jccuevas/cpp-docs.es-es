---
title: En función de punteros (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __based
- __based_cpp
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afecaafc5a9d3c1eb9a9466cce303a493d355ce0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196212"
---
# <a name="based-pointers-c"></a>Punteros con base (C++)
**Específicos de Microsoft**  
  
 El **__based** palabra clave permite declarar punteros basados en punteros (punteros que son desplazamientos de punteros existentes).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
type __based( base ) declarator   
```  
  
## <a name="remarks"></a>Comentarios  
 Los punteros basados en direcciones de puntero son la única forma de la **__based** palabra clave válida en compilaciones de 32 bits o 64 bits. Para el compilador de 32 bits de Microsoft C/C++, un puntero basado es un desplazamiento de 32 bits desde una base de puntero de 32 bits. Se aplica una restricción similar a los entornos de 64 bits, donde un puntero basado es un desplazamiento de 64 bits de la base de 64 bits.  
  
 Uno de los usos de los punteros basados en punteros son los identificadores persistentes que contienen punteros. Una lista vinculada formada por punteros basados en un puntero se puede guardar en el disco y recargar en otro lugar de la memoria; los punteros seguirán siendo válidos. Por ejemplo:  
  
```cpp 
// based_pointers1.cpp  
// compile with: /c  
void *vpBuffer;  
struct llist_t {  
   void __based( vpBuffer ) *vpData;  
   struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 Al puntero `vpBuffer` se le asigna la dirección de memoria asignada posteriormente en el programa. La lista vinculada se reubica en relación con el valor de `vpBuffer`.  
  
> [!NOTE]
>  También pueden realizarse mediante el uso de los identificadores persistentes que contienen punteros [archivos asignados a memoria](/windows/desktop/Memory/file-mapping).  
  
 Cuando se desreferencia un puntero basado, la base se debe especificar explícitamente o se debe conocer implícitamente con la declaración.  
  
 Para ofrecer compatibilidad con versiones anteriores, **_basado** es un sinónimo de **__based**.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo se cambia un puntero basado mediante el cambio de su base.  
  
```cpp 
// based_pointers2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int a1[] = { 1,2,3 };  
int a2[] = { 10,11,12 };  
int *pBased;  
  
typedef int __based(pBased) * pBasedPtr;  
  
using namespace std;  
int main() {  
   pBased = &a1[0];  
   pBasedPtr pb = 0;  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
  
   pBased = &a2[0];  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
}  
```  
  
```Output  
1  
2  
10  
11  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [alloc_text](../preprocessor/alloc-text.md)