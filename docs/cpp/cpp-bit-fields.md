---
title: Campos de bits de C++ | Documentos de Microsoft
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
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff6b2a37c511313bd129705da38e66380e89edae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-bit-fields"></a>Campos de bits de C++
Las clases y estructuras pueden contener miembros que ocupan menos almacenamiento que un tipo entero. Estos miembros se especifican como campos de bits. La sintaxis de un campo de bits *declarador de miembro* especificación se indica a continuación:  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
declarator  : constant-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 El `declarator` (opcional) es el nombre por el que se obtiene acceso al miembro en el programa. Debe ser de tipo entero (incluidos los tipos enumerados). El *expresión constante* especifica el número de bits que ocupa el miembro de la estructura. Se pueden utilizar campos de bits anónimos (es decir, miembros de campos de bits sin identificador) para rellenar.  
  
> [!NOTE]
>  Un campo de bits sin nombre de ancho 0 fuerza la alineación del campo de bits siguiente al límite siguiente de `type`, donde `type` es el tipo del miembro.  
  
 En el ejemplo siguiente se declara una estructura que contiene campos de bits:  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 En la ilustración siguiente se muestra el diseño de memoria conceptual de un objeto de tipo `Date`.  
  
 ![Diseño de memoria de un objeto de fecha](../cpp/media/vc38uq1.png "vc38UQ1")  
Diseño de memoria de objeto de fecha  
  
 Tenga en cuenta que `nYear` tiene una longitud de 8 bits y que desbordaría el límite de palabras del tipo declarado, **entero corto sin signo**. Por lo tanto, comienza al principio de un nuevo **entero corto sin signo**. No es necesario que todos los campos de bits quepan en un objeto del tipo subyacente; se asignan nuevas unidades de almacenamiento según el número de bits solicitados en la declaración.  
  
 **Específicos de Microsoft**  
  
 El orden de los datos declarados como campos de bits es de bit bajo a bit alto, como se muestra en la ilustración anterior.  
  
 **FIN de Específicos de Microsoft**  
  
 Si la declaración de una estructura incluye un campo sin nombre de longitud 0, como se muestra en el ejemplo siguiente,  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 el diseño de memoria es el que se muestra en la ilustración siguiente.  
  
 ![Diseño de objeto de fecha con cero &#45; campo de bits de longitud](../cpp/media/vc38uq2.png "vc38UQ2")  
Diseño de objeto de fecha con campo de bits de longitud cero  
  
 El tipo subyacente de un campo de bits debe ser un tipo entero, como se describe en [tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
## <a name="restrictions-on-bit-fields"></a>Restricciones de los campos de bits  
 En la lista siguiente se detallan operaciones erróneas en campos de bits:  
  
1.  Tomar la dirección de un campo de bits.  
  
2.  Inicializar una referencia con un campo de bits.  
  
## <a name="see-also"></a>Vea también  
 [Clases y structs](../cpp/classes-and-structs-cpp.md)