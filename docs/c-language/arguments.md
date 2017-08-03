---
title: Argumentos | Microsoft Docs
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
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
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
ms.openlocfilehash: f755a77679348085f5b5ceb38665351221889c7b
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="arguments"></a>Argumentos
Los argumentos de una llamada a función tienen este formato:  
  
```  
  
expression  
(  
expression-list <SUB>opt</SUB> )  /* Function call */  
```  
  
 En una llamada a función, *expression-list* es una lista de expresiones (separadas por comas). Los valores de estas últimas expresiones son los argumentos pasados a la función. Si la función no toma ningún argumento, *expression-list* debe contener la palabra clave `void`.  
  
 Un argumento puede ser cualquier valor de tipo fundamental, estructura, unión o puntero. Todos los argumentos se pasan por valor. Esto significa que se asigna una copia del argumento al parámetro correspondiente. La función no conoce la ubicación de memoria real del argumento pasado. La función utiliza esta copia sin afectar a la variable de la que se derivó originalmente.  
  
 Aunque no puede pasar matrices o funciones como argumentos, puede pasar punteros a estos elementos. Los punteros son una manera de que una función acceda a un valor por referencia. Puesto que un puntero a una variable contiene la dirección de la variable, la función puede usar esta dirección para tener acceso al valor de la variable. Los argumentos de puntero permiten que una función obtenga acceso a las matrices y funciones, aunque las matrices y funciones no se pueden pasar como argumentos.  
  
 El orden en que se evalúan los argumentos puede variar según los distintos compiladores y niveles de optimización. Sin embargo, los argumentos y sus posibles efectos secundarios se evalúan completamente antes de que se especifique la función. Vea [Efectos secundarios](../c-language/side-effects.md) para obtener información sobre los efectos secundarios.  
  
 El elemento *expression-list* en una llamada a función se evalúa y se realizan las conversiones aritméticas habituales en cada argumento de la llamada a función. Si hay un prototipo disponible, el tipo de argumento resultante se compara con el parámetro correspondiente del prototipo. Si no coinciden, se realiza una conversión o se emite un mensaje de diagnóstico. Los parámetros también se someten a las conversiones aritméticas usuales.  
  
 El número de expresiones en *expression-list* debe coincidir con el número de parámetros, a menos que el prototipo o la definición de la función especifique explícitamente un número variable de argumentos. En este caso, el compilador comprueba tantos argumentos como nombres de tipo haya en la lista de parámetros y los convierte, si es necesario, como se ha descrito anteriormente. Vea [Llamadas con un número variable de argumentos](../c-language/calls-with-a-variable-number-of-arguments.md) para obtener más información.  
  
 Si la lista de parámetros del prototipo solo contiene la palabra clave `void`, el compilador no espera ningún argumento en la llamada a función y ningún parámetro en la definición. Si encuentra algún argumento, se emite un mensaje de diagnóstico.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usan punteros como argumentos:  
  
```  
int main()  
{  
    /* Function prototype */  
  
    void swap( int *num1, int *num2 );  
    int x, y;  
    .  
    .  
    .  
    swap( &x, &y );  /* Function call */  
}  
  
/* Function definition */  
  
void swap( int *num1, int *num2 )  
{  
    int t;  
  
    t = *num1;  
    *num1 = *num2;  
    *num2 = t;  
}  
```  
  
 En este ejemplo, la función `swap` se declara en `main` con dos argumentos, representados respectivamente por los identificadores `num1` y `num2`, que son punteros a valores `int`. Los parámetros `num1` y `num2` en la definición de tipo prototipo también se declaran como punteros a valores de tipo `int`.  
  
 En la llamada a función  
  
```  
swap( &x, &y )  
```  
  
 la dirección de `x` se almacena en `num1` y la dirección de `y` se almacena en `num2`. Ahora existen dos nombres, o "alias", para la misma ubicación. Las referencias a `*num1` y `*num2` en `swap` son en efecto referencias a `x` e `y` en `main`. Las asignaciones de `swap` en realidad intercambian el contenido de `x` e `y`. Por consiguiente, no se necesita ninguna instrucción `return`.  
  
 El compilador realiza la comprobación de tipos en los argumentos de `swap` porque el prototipo de `swap` incluye tipos de argumento para cada parámetro. Los identificadores dentro de los paréntesis del prototipo y la definición pueden ser iguales o diferentes. Lo importante es que los tipos de los argumentos coincidan con los de las listas de parámetros del prototipo y la definición.  
  
## <a name="see-also"></a>Vea también  
 [Llamadas de función](../c-language/function-calls.md)
