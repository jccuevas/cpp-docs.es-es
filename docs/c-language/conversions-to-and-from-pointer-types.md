---
title: Conversiones entre tipos de puntero | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1751c19ba222bbdf9dfc30a290201289db1af850
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-to-and-from-pointer-types"></a>Conversiones entre tipos de puntero
Un puntero a un tipo de valor se puede convertir en un puntero a un tipo diferente. Sin embargo, el resultado puede ser indefinido debido a los requisitos de alineación y a los tamaños de los tipos diferentes en el almacenamiento. Un puntero a un objeto se puede convertir en un puntero a un objeto cuyo tipo requiere una alineación de almacenamiento igual o menos estricta, y viceversa, sin necesidad de hacer cambios.  
  
 Un puntero a `void` se puede convertir a o desde un puntero a cualquier tipo, sin restricción ni pérdida de información. Si el resultado se convierte de nuevo al tipo original, se recupera el puntero original.  
  
 Si un puntero se convierte en otro puntero con el mismo tipo pero con calificadores diferentes o adicionales, el nuevo puntero es igual que el anterior, salvo por las restricciones impuestas por el nuevo calificador.  
  
 Un valor de puntero también se puede convertir en un valor entero. La ruta de conversión depende del tamaño del puntero y del tamaño del tipo entero, de acuerdo con las reglas siguientes:  
  
-   Si el tamaño del puntero es mayor o igual que el tamaño del tipo entero, el puntero se comporta como un valor sin signo en la conversión, con la salvedad de que no se puede convertir en un valor flotante.  
  
-   Si el puntero es menor que el tipo entero, el puntero se convierte en primer lugar en un puntero con el mismo tamaño que el tipo entero y después se convierte en el tipo entero.  
  
 De igual modo, un tipo entero puede convertirse en un tipo de puntero según las reglas siguientes:  
  
-   Si el tipo entero tiene el mismo tamaño que el tipo de puntero, la conversión simplemente hace que el valor entero se trate como un puntero (un entero sin signo).  
  
-   Si el tamaño del tipo entero es diferente del tamaño del tipo de puntero, el tipo entero se convierte primero al tamaño de puntero, mediante las rutas de conversión incluidas en las tablas [Conversión de tipos enteros con signo](../c-language/conversions-from-signed-integral-types.md) y [Conversión de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md). A continuación, se trata como un valor de puntero.  
  
 Una expresión constante entera con valor 0 o como una conversión de expresión al tipo **void \*** se puede convertir mediante una conversión de tipo, mediante asignación o mediante comparación en un puntero de cualquier tipo. Esto genera un puntero null que es igual a otro puntero null del mismo tipo, pero este puntero null no es igual a ningún puntero a una función o a un objeto. Los enteros distintos de la constante 0 se pueden convertir al tipo de puntero, pero el resultado no es transferible.  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)