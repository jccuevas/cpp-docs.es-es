---
title: "Resumen de reglas de &#225;mbito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nombres de clase [C++], reglas de ámbito"
  - "ámbito de clase [C++], reglas"
  - "clases [C++], ámbito"
  - "nombres [C++], class"
  - "ámbito [C++], nombres de clase"
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Resumen de reglas de &#225;mbito
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso de un nombre debe ser inequívoco dentro de su ámbito \(hasta el punto en que se determina la sobrecarga\).  Si el nombre indica una función, la función no debe ser ambigua respecto al número y tipo de parámetros.  Si el nombre se mantiene no ambiguo, se aplican las reglas de [acceso a miembros](../cpp/member-access-control-cpp.md).  
  
## Inicializadores del constructor  
 Los inicializadores de constructor \(descritos en [Inicialización de bases y miembros](http://msdn.microsoft.com/es-es/2f71377e-2b6b-49da-9a26-18e9b40226a1)\) se evalúan en el ámbito del bloque más externo del constructor para el que se especifican.  Por lo tanto, pueden usar los nombres de parámetro del constructor.  
  
## Nombres globales  
 Un nombre de un objeto, una función o un enumerador es global si se presenta fuera de cualquier función o clase o está precedido por el operador unario global de ámbito \(`::`\) y si no se usa junto con alguno de estos operadores binarios:  
  
-   Resolución de ámbito \(`::`\)  
  
-   Selección de miembro para objetos y referencias \(**.**\)  
  
-   Selección de miembro para punteros \(**–\>**\)  
  
## Nombres completos  
 Los nombres utilizados con el operador binario de resolución de ámbito \(`::`\) se denominan “nombres completos”. El nombre especificado detrás del operador binario de resolución de ámbito debe ser un miembro de la clase especificada a la izquierda del operador o un miembro de su clase o clases base.  
  
 Los nombres especificados detrás del operador de selección de miembro \(**.** o **–\>**\) deben ser miembros del tipo de clase del objeto especificado a la izquierda del operador o miembros de su clase o clases base.  Los nombres especificados a la derecha del operador de selección de miembro \(**–\>**\) también pueden ser objetos de otro tipo de clase, siempre que el lado izquierdo de **–\>** sea un objeto de clase y que la clase defina un operador de selección de miembro sobrecargado \(**–\>**\) que se evalúe como un puntero a otro tipo de clase.  \(Esta especificación se explica con más detalle en [Acceso a miembros de clase](../cpp/member-access.md)\).  
  
 El compilador busca los nombres en el orden siguiente y se detiene cuando encuentra el nombre:  
  
1.  El ámbito de bloque actual si el nombre se utiliza dentro de una función; en caso contrario, el ámbito global.  
  
2.  En el exterior, a través de cada ámbito de bloque contenedor, incluido el ámbito de función más externo \(que incluye parámetros de función\).  
  
3.  Si el nombre se utiliza dentro de una función miembro, se busca el nombre en el ámbito de la clase.  
  
4.  El nombre se busca en las clases base de la clase.  
  
5.  Se busca en el ámbito de la clase anidada contenedora y en sus clases base.  La búsqueda continúa hasta que se busque en el ámbito de la clase contenedora más externo.  
  
6.  Se busca en el ámbito global.  
  
 Sin embargo, puede modificar este orden de búsqueda de la forma siguiente:  
  
1.  Los nombres precedidos por `::` obligan a que la búsqueda se inicie en el ámbito global.  
  
2.  Los nombres precedidos por las palabras clave **class**, `struct` y **union** fuerzan al compilador a buscar solo los nombres de **class**, `struct` o **union**.  
  
3.  Los nombres del lado izquierdo del operador de resolución de ámbito \(`::`\) solo pueden ser nombres **class**, `struct`, **namespace** o **union**.  
  
 Si el nombre hace referencia a un miembro no estático pero se utiliza en una función miembro estática, se genera un mensaje de error.  De igual forma, si el nombre hace referencia a algún miembro no estático en una clase contenedora, se genera un mensaje de error, porque las clases contenidas no tienen punteros **this** de la clase contenedora.  
  
## Nombres de parámetro de la función  
 Los nombres de los parámetros de función en las definiciones de función se consideran que están en el ámbito del bloque más externo de la función.  Por consiguiente, son nombres locales y salen del ámbito cuando termina la función.  
  
 Los nombres de los parámetros de función en las declaraciones de función \(prototipos\) están en el ámbito local de la declaración y salen del ámbito al final de la declaración.  
  
 Los parámetros predeterminados están en el ámbito del parámetro para el que son el parámetro predeterminado, como se describe en los dos párrafos anteriores.  Sin embargo, no pueden acceder a variables locales o miembros de clase no estáticos.  Los parámetros predeterminados se evalúan en el punto de la llamada de función, pero se evalúan en el ámbito original de la declaración de función.  Por tanto, los parámetros predeterminados de funciones miembro siempre se evalúan en el ámbito de la clase.  
  
## Vea también  
 [Herencia](../cpp/inheritance-cpp.md)