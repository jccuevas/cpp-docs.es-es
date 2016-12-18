---
title: "switch (Instrucci&#243;n) (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "switch"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "switch (palabra clave) [C]"
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# switch (Instrucci&#243;n) (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones `switch` y **case** ayudan a controlar las operaciones condicionales y de bifurcación complejas.  La instrucción `switch` transfiere el control a una instrucción dentro del cuerpo.  
  
## Sintaxis  
 *selection\-statement*:  
 **switch \(** *expression* **\)** *statement*  
  
 *labeled\-statement*:  
 **case**  *constant\-expression*  **:**  *statement*  
  
 **default:**  *statement*  
  
 El control pasa a la instrucción cuya *constant\-expression* **case** coincida con el valor de **switch \(** *expression* **\)**.  La instrucción `switch` puede incluir cualquier número de instancias de **case**, pero dos constantes case no pueden tener el mismo valor dentro de la misma instrucción `switch`.  La ejecución del cuerpo de instrucción comienza en la instrucción seleccionada y continúa hasta el final del cuerpo o hasta que una instrucción **break** transfiere el control fuera del cuerpo.  
  
 El uso de la instrucción `switch` suele tener una apariencia similar a lo siguiente:  
  
 `switch` \( *expression* \)  
  
 **{**  
  
 *declaraciones*  
  
 .  
  
 .  
  
 .  
  
 **case** *constant\-expression* **:**  
  
 *instrucciones ejecutadas si la expresión es igual al*  
  
 *valor de esta expresión constante*  
  
 .  
  
 .  
  
 .  
  
 **break;**  
  
 **default:**  
  
 *instrucciones ejecutadas si la expresión no es igual a*  
  
 *cualquier expresión constante case*  
  
 **}**  
  
 Puede utilizar la instrucción **break** para finalizar el procesamiento de una expresión case concreta dentro de la instrucción `switch` y para bifurcar al final de la instrucción `switch`.  Sin **break**, el programa continúa a la siguiente expresión case y ejecuta las instrucciones hasta un **break** o hasta que se alcance el final de la instrucción.  En algunas situaciones, esta continuación puede ser deseable.  
  
 Se ejecuta la instrucción **default** si ninguna *constant\-expression* **case** es igual al valor de **switch \(** *expression* **\)**.  Si se omite la instrucción **default** y no se encuentra ninguna coincidencia de **case**, no se ejecuta ninguna de las instrucciones del cuerpo de `switch`.  Puede haber a lo sumo una instrucción **default**.  No es necesario que la instrucción **default** esté al final; puede aparecer en cualquier parte del cuerpo de la instrucción `switch`.  Una etiqueta **case** o **default** solo puede aparecer en una instrucción `switch`.  
  
 El tipo de la *expression* `switch` y de la *constant\-expression* **case** debe ser entero.  El valor de cada *constant\-expression* **case** debe ser único dentro del cuerpo de instrucción.  
  
 Las etiquetas **case** y **default** del cuerpo de instrucción de `switch` solo tienen sentido en la prueba inicial que determina dónde se inicia la ejecución en el cuerpo de instrucción.  Las instrucciones switch pueden anidarse.  Cualquier variable estática se inicializa antes de ejecutar cualquier instrucción `switch`.  
  
> [!NOTE]
>  Las declaraciones pueden aparecer en el encabezado de la instrucción compuesta que constituye el cuerpo de `switch`, pero las inicializaciones incluidas en las declaraciones no se realizan.  La instrucción `switch` transfiere el control directamente a una instrucción ejecutable dentro del cuerpo y omite las líneas que contienen inicializaciones.  
  
 En los siguientes ejemplos de código se muestran instrucciones `switch`:  
  
```  
switch( c )   
{  
    case 'A':  
        capa++;  
    case 'a':  
        lettera++;  
    default :  
        total++;  
}  
```  
  
 En este ejemplo, las tres instrucciones del cuerpo de `switch` se ejecutan si `c` es igual a `'A'`, ya que no aparece una instrucción **break** antes de la siguiente expresión case.  El control de la ejecución se transfiere a la primera instrucción \(`capa++;`\) y continúa en orden con el resto del cuerpo.  Si `c` es igual a `'a'`, se incrementan `lettera` y `total`.  Solo se incrementa `total` si `c` no es igual a `'A'` o `'a'`.  
  
```  
switch( i )   
{  
    case -1:  
        n++;  
        break;  
    case 0 :  
        z++;  
        break;  
    case 1 :  
        p++;  
        break;  
}  
```  
  
 En este ejemplo, una instrucción **break** sigue a cada instrucción del cuerpo de `switch`.  La instrucción **break** fuerza una salida del cuerpo de instrucción tras ejecutar una instrucción.  Si `i` es igual a – 1, solo se incrementa `n`.  La instrucción **break** que sigue a la instrucción `n++;` hace que el control de la ejecución salga del cuerpo de instrucción y omita las instrucciones restantes.  De igual forma, si `i` es igual a 0, solo se incrementa `z`; si `i` es igual a 1, solo se incrementa `p`.  La instrucción **break** final no es estrictamente necesaria, puesto que el control sale del cuerpo al final de la instrucción compuesta, pero se incluye por coherencia.  
  
 Una sola instrucción puede contener varias etiquetas **case**, como se muestra en el ejemplo siguiente:  
  
```  
case 'a' :  
case 'b' :  
case 'c' :  
case 'd' :  
case 'e' :  
case 'f' :  hexcvt(c);  
```  
  
 En este ejemplo, si *constant\-expression* es cualquier letra entre `'a'` y `'f'`, se llama a la función `hexcvt`.  
  
 **Específicos de Microsoft**  
  
 Microsoft C no limita el número de valores case en una instrucción `switch`.  El número solo está limitado por la memoria disponible.  ANSI C requiere que al menos 257 etiquetas case se permitan en una instrucción `switch`.  
  
 El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas.  Utilice la opción de compilador \/Za para deshabilitar estas extensiones.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [switch \(Instrucción\) \(C\+\+\)](../cpp/switch-statement-cpp.md)