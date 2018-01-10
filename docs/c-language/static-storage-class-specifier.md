---
title: static (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c957b78eeb506e9f1f91a670cf5cc4d52ad72878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="static-storage-class-specifier"></a>static (Especificador de clase de almacenamiento)
Una variable declarada en el nivel interno con el especificador de clase de almacenamiento **static** tiene una duración global pero solo es visible dentro del bloque en el que se declara. Para las cadenas constantes, el uso de **static** es útil porque palía la sobrecarga de inicialización frecuente en funciones invocadas con frecuencia.  
  
## <a name="remarks"></a>Comentarios  
Si no se inicializa explícitamente una variable **static**, se inicializa en 0 de forma predeterminada. Dentro de una función, **static** hace que el almacenamiento se asigne y actúa como una definición. Las variables estáticas internas proporcionan almacenamiento permanente privado que es visible solamente a una única función.  
  
## <a name="see-also"></a>Vea también  
[Clases de almacenamiento de C](c-storage-classes.md)  
[Clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md)  