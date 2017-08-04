---
title: Funciones recursivas | Microsoft Docs
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
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 38d98e568b88d8b26be2a04a9b643fb0d99a9712
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="recursive-functions"></a>Funciones recursivas
En un programa de C, se puede llamar a cualquier función de forma recursiva, es decir, cualquier función se puede llamar a sí misma. El número de llamadas recursivas viene limitado por el tamaño de la pila. Vea la opción del vinculador [/STACK (asignaciones de pila)](../build/reference/stack-stack-allocations.md) (/STACK) para obtener información sobre las opciones del vinculador que establecen el tamaño de la pila. Cada vez que se llama a la función, se asigna nuevo almacenamiento para los parámetros y para las variables **auto** y **register** para que no se sobrescriban sus valores en llamadas anteriores que no han finalizado. Los parámetros solo son accesibles directamente para la instancia de la función en la que se crean. Los parámetros anteriores no son directamente accesibles para las siguientes instancias de la función.  
  
 Tenga en cuenta que las variables declaradas con almacenamiento **static** no requieren nuevo almacenamiento con cada llamada recursiva. Su almacenamiento existe durante la vigencia del programa. Cada referencia a estas variables accede a la misma área de almacenamiento.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se ilustran las llamadas recursivas:  
  
```  
int factorial( int num );      /* Function prototype */  
  
int main()  
{  
    int result, number;  
    .  
    .  
    .  
    result = factorial( number );  
}  
  
int factorial( int num )      /* Function definition */  
{  
    .  
    .  
    .  
    if ( ( num > 0 ) || ( num <= 10 ) )  
        return( num * factorial( num - 1 ) );  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Llamadas de función](../c-language/function-calls.md)
