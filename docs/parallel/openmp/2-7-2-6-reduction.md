---
title: "2.7.2.6 reduction | Microsoft Docs"
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
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.6 reduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta cláusula realiza una reducción en variables escalares que aparecen en *variable\-lista*, con el operador Op. Sys.  La sintaxis de la cláusula de `reduction` es la siguiente:  
  
```  
  
reduction(  
op  
:  
variable-list  
)  
  
```  
  
 Un informe detallado se especifica normalmente para una instrucción con una de las siguientes formas:  
  
```  
  
        x     =  x     op     expr  
x     binop=  expr  
x     =  expr     op     x            (except for subtraction)  
x++  
++x  
x--  
--x  
```  
  
 donde:  
  
 *x*  
 Una de las variables de informe especificadas en `list`.  
  
 *variable\-lista*  
 Una lista separada por comas de variables escalares de reducción.  
  
 *expr*  
 Una expresión con el escalar escribe que no hace referencia al *X.*  
  
 `op`  
 No un operador sobrecargado pero uno de \+, \*, \-, y, ^, &#124;, &&, o &#124;&#124;.  
  
 `binop`  
 No un operador sobrecargado pero uno de \+, \*, \-, y, ^, o &#124;.  
  
 A continuación se muestra un ejemplo de cláusula de `reduction` :  
  
```  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
 Como se muestra en el ejemplo, un operador puede ocultar dentro de una llamada de función.  El usuario debe tener cuidado del operador especificado en las coincidencias de la cláusula de `reduction` la operación de reducción.  
  
 Aunque el operando derecho de &#124;&#124; el operador no tiene efecto secundario en este ejemplo, se permite, pero se debe utilizar con cuidado.  En este contexto, un efecto secundario que se garantiza que no aparezca durante la ejecución secuencial de bucle puede producir durante la ejecución en paralelo.  Esta diferencia puede producirse porque el orden de ejecución de las iteraciones es indeterminado.  
  
 El operador se utiliza para determinar el valor inicial de cualquier variable privada utilizada por el compilador para el informe detallado y para determinar el operador de finalización.  Especificar el operador explícitamente permite que la instrucción de reducción está fuera de la extensión léxica de construcción.  Cualquier número de cláusulas de `reduction` se puede especificar en la directiva, pero una variable puede aparecer en al menos una cláusula de `reduction` para esa directiva.  
  
 Una copia privada de cada variable de *variable\-lista* se crea, una para cada subproceso, como si la cláusula de `private` se hubiera utilizada.  La copia privada inicializa según el operador \(vea la tabla siguiente\).  
  
 Al final de la región para la que la cláusula de `reduction` se especificó, el objeto original se actualiza para reflejar el resultado de combinar su valor original con el valor final de cada una de las copias privadas mediante el operador especificado.  Los operadores son todos de reducción asociativos \(a excepción de resta\), el compilador puede reasociar libremente el cálculo del valor final.  \(Los resultados parciales de una reducción de la resta se agregan para formar el valor final\).  
  
 El valor del objeto original deja de ser indeterminado cuando permanece el primer subproceso alcanza la cláusula que contiene y tan hasta que se completa el cálculo de reducción.  Normalmente, el cálculo se completo al final de la construcción; sin embargo, si la cláusula de `reduction` se utiliza en una construcción a la que `nowait` también se aplique, el valor del objeto original permanece indeterminado hasta que una sincronización de barrera se haya realizado para garantizar que todos los subprocesos han completado la cláusula de `reduction` .  
  
 La tabla siguiente enumera los operadores que son válidos y sus valores canónicos de inicialización.  El valor real de inicialización será coherente con el tipo de datos de la variable de reducción.  
  
|Operador|Inicialización|  
|--------------|--------------------|  
|\+|0|  
|\*|1|  
|\-|0|  
|&|~0|  
|&#124;|0|  
|^|0|  
|&&|1|  
|&#124;&#124;|0|  
  
 Restricciones de la cláusula de `reduction` son los siguientes:  
  
-   El tipo de las variables en la cláusula de `reduction` debe ser válido para el operador de informe salvo que los tipos de puntero y los tipos de referencia no permite.  
  
-   Una variable que se especifica en la cláusula de `reduction` no debe ser **const**\- completo.  
  
-   Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula de `reduction` de una directiva de **Paralelo** no se pueden especificar en una cláusula de `reduction` en una directiva de división del trabajo que se enlaza a la construcción paralela.  
  
    ```  
    #pragma omp parallel private(y)  
    { /* ERROR - private variable y cannot be specified  
                 in a reduction clause */  
       #pragma omp for reduction(+: y)  
       for (i=0; i<n; i++)  
          y += b[i];  
    }  
  
    /* ERROR - variable x cannot be specified in both  
               a shared and a reduction clause */  
    #pragma omp parallel for shared(x) reduction(+: x)  
    ```