---
title: Almacenamiento de campos de bits
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 7aa6e02c347ff14bb0552320567b343c7215ebc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499094"
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