---
title: "Almacenamiento y alineación de estructuras | Microsoft Docs"
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
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 8a0f7231b8c3e3f15e650044164c55b42d159c6b
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="storage-and-alignment-of-structures"></a>Almacenamiento y alineación de estructuras
**Específicos de Microsoft**  
  
 Los miembros de estructura se almacenan secuencialmente en el orden en que se declaran: el primer miembro tiene la dirección de memoria menor y el último miembro, la dirección de memoria mayor.  
  
 Cada objeto de datos tiene un elemento *alignment-requirement*. Para las estructuras, el requisito es el mayor de sus miembros. A cada objeto se le asigna un *offset*, de forma que se cumpla lo siguiente:  
  
 *offset* `%` *alignment-requirement* `==` 0  
  
 Los campos de bits adyacentes se empaquetan en la misma unidad de asignación de 1, 2 o 4 bytes si los tipos enteros tienen el mismo tamaño y si el siguiente campo de bits cabe en la unidad de asignación actual sin traspasar el límite impuesto por los requisitos comunes de alineación de los campos de bits.  
  
 Para conservar espacio o para ajustarse a las estructuras de datos existentes, quizás desee almacenar las estructuras de forma más o menos compacta. La opción del compilador [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] y [#pragma pack](../preprocessor/pack.md) controlan cómo se "empaquetan" los datos de la estructura en memoria. Si utiliza la opción /Zp[*n*], donde *n* es 1, 2, 4, 8 o 16, cada miembro de la estructura detrás del primero se almacena en los límites de bytes que son el requisito de alineación del campo o el tamaño de empaquetado (*n*), lo que sea menor. Expresados como fórmula, los límites de bytes son  
  
```  
min( n, sizeof( item ) )  
```  
  
 donde *n* es el tamaño de empaquetado expresado con la opción /Zp[*n*] e *item* es el miembro de la estructura. El tamaño de empaquetado predeterminado es /Zp8.  
  
 Si desea utilizar la instrucción pragma `pack` para especificar un empaquetado distinto del empaquetado especificado en la línea de comandos para una estructura determinada, especifique la instrucción pragma `pack`, con el tamaño de empaquetado 1, 2, 4, 8 o 16, delante de la estructura. Para restablecer el empaquetado especificado en la línea de comandos, especifique la instrucción pragma `pack` sin argumentos.  
  
 Los campos de bits tienen como valor predeterminado el tamaño **long** en el compilador de C de Microsoft. Los miembros de la estructura se alinean de acuerdo con el tamaño del tipo o el tamaño de /Zp[*n*], lo que sea menor. El tamaño predeterminado es 4.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de estructura](../c-language/structure-declarations.md)
