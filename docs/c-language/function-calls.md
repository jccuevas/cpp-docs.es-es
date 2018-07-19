---
title: Llamadas de función | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de77f98010bec66993585d8cc998ced489ebadf7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387868"
---
# <a name="function-calls"></a>Llamadas de función
Una *llamada a función* es una expresión que pasa el control y los argumentos (si existen) a una función, y tiene el formato:  
  
 *expression* (*expression-list*opt)  
  
 donde *expression* es un nombre de función o se evalúa como una dirección de función y *expression-list* es una lista de expresiones (separadas por comas). Los valores de estas últimas expresiones son los argumentos pasados a la función. Si la función no devuelve un valor, se declara como una función que devuelve `void`.  
  
 Si existe una declaración antes de la llamada a función pero no se proporciona ninguna información sobre los parámetros, los argumentos sin declarar simplemente se someten a las conversiones aritméticas habituales.  
  
> [!NOTE]
>  Las expresiones de la lista de argumentos de función se pueden evaluar en cualquier orden, por lo que los argumentos cuyos valores pueden cambiar debido a efectos secundarios de otro argumento tienen valores sin definir. El punto de secuencia definido por el operador de llamada a función solo garantiza que todos los efectos secundarios en la lista de argumentos se evalúen antes de que el control pase a la función llamada. (Observe que el orden de inserción de los argumentos en la pila es otra cuestión). Vea [Puntos de secuencia de C](../c-language/c-sequence-points.md) para obtener más información.  
  
 El único requisito de cualquier llamada a función es que la expresión que va antes del paréntesis se debe evaluar como una dirección de función. Esto significa que una función se puede llamar a través de cualquier expresión de puntero a función.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestran llamadas a función llamadas desde una instrucción `switch`:  
  
```  
int main()  
{  
    /* Function prototypes */  
  
    long lift( int ), step( int ), drop( int );  
    void work( int number, long (*function)(int i) );  
  
    int select, count;  
    .  
    .  
    .  
    select = 1;  
    switch( select )   
    {  
        case 1: work( count, lift );  
                break;  
  
        case 2: work( count, step );  
                break;  
  
        case 3: work( count, drop );  
                /* Fall through to next case */  
        default:  
                break;  
    }  
}  
  
/* Function definition */  
  
void work( int number, long (*function)(int i) )  
{  
    int i;  
    long j;  
  
    for ( i = j = 0; i < number; i++ )  
            j += ( *function )( i );  
}  
```  
  
 En este ejemplo, la llamada a función en `main`,  
  
```  
work( count, lift );  
```  
  
 pasa una variable de entero, `count`, y la dirección de la función `lift` a la función `work`. Observe que la dirección de función se pasa simplemente mediante el identificador de función, ya que un identificador de función se evalúa como una expresión de puntero. Para utilizar un identificador de función de esta manera, la función debe declararse o definirse antes de utilizar el identificador; si no, el identificador no se reconoce. En este caso, se proporciona un prototipo para `work` al principio de la función `main`.  
  
 El parámetro `function` en `work` se declara como puntero a una función que toma un argumento `int` y que devuelve un valor **long**. Los paréntesis que rodean el nombre del parámetro son necesarios; sin ellos, la declaración especificaría una función que devuelve un puntero a un valor **long**.  
  
 La función `work` llama a la función seleccionada desde dentro del bucle **for** mediante la siguiente llamada a función:  
  
```  
( *function )( i );  
```  
  
 Un argumento, `i`, se pasa a la función llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../c-language/functions-c.md)