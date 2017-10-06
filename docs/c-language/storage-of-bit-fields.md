---
title: Almacenamiento de campos de bits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b0e25945ff20adcccce060363601cfc1a1a1f6fd
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="storage-of-bit-fields"></a>Almacenamiento de campos de bits
**ANSI 3.5.2.1** El orden de asignación de campos de bits en un entero  
  
 Los campos de bits se asignan dentro de un entero del bit menos significativo al bit más significativo. En el código siguiente  
  
```  
struct mybitfields  
{  
   unsigned a : 4;  
   unsigned b : 5;  
   unsigned c : 7;  
} test;  
  
int main( void )  
{  
   test.a = 2;  
   test.b = 31;  
   test.c = 0;  
}  
```  
  
 los bits se organizan de esta forma:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Puesto que los procesadores 80x86 almacenan el byte bajo de los valores enteros antes que el byte alto, el entero 0x01F2 anterior se almacenaría en la memoria física como 0xF2 seguido de 0x01.  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)
