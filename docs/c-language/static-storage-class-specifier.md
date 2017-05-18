---
title: static (Especificador de clase de almacenamiento) | Microsoft Docs
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
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 7
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 34f60570d18882ddfb7ebef78977d6b2f5c82000
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="static-storage-class-specifier"></a>static (Especificador de clase de almacenamiento)
Una variable declarada en el nivel interno con el especificador de clase de almacenamiento **static** tiene una duración global pero solo es visible dentro del bloque en el que se declara. Para las cadenas constantes, el uso de **static** es útil porque palía la sobrecarga de inicialización frecuente en funciones invocadas con frecuencia.  
  
## <a name="remarks"></a>Comentarios  
Si no se inicializa explícitamente una variable **static**, se inicializa en 0 de forma predeterminada. Dentro de una función, **static** hace que el almacenamiento se asigne y actúa como una definición. Las variables estáticas internas proporcionan almacenamiento permanente privado que es visible solamente a una única función.  
  
## <a name="see-also"></a>Vea también  
[Clases de almacenamiento de C](c-storage-classes.md)  
[Clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md)  
