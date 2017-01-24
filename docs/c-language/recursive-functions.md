---
title: "Funciones recursivas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "llamadas a funciones, recursivos"
  - "funciones [C], llamar de forma recursiva"
  - "funciones [C], recursivos"
  - "llamadas a funciones recursivas"
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones recursivas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En un programa de C, se puede llamar a cualquier función de forma recursiva, es decir, cualquier función se puede llamar a sí misma.  El número de llamadas recursivas viene limitado por el tamaño de la pila.  Vea la opción del vinculador [\/STACK \(Asignaciones de la pila\)](../build/reference/stack-stack-allocations.md) \(\/STACK\) para obtener información sobre las opciones del vinculador que establecen el tamaño de la pila.  Cada vez que se llama a la función, se asigna nuevo almacenamiento para los parámetros y para las variables **auto** y **register** para que no se sobrescriban sus valores en llamadas anteriores que no han finalizado.  Los parámetros solo son accesibles directamente para la instancia de la función en la que se crean.  Los parámetros anteriores no son directamente accesibles para las siguientes instancias de la función.  
  
 Tenga en cuenta que las variables declaradas con almacenamiento **static** no requieren nuevo almacenamiento con cada llamada recursiva.  Su almacenamiento existe durante la vigencia del programa.  Cada referencia a estas variables accede a la misma área de almacenamiento.  
  
## Ejemplo  
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
  
## Vea también  
 [Llamadas de función](../c-language/function-calls.md)