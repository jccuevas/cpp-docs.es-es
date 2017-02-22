---
title: "Espacios de nombres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "etiquetas de enumeración"
  - "espacios de nombres [C++]"
  - "nombres [C++], elementos declarados"
  - "etiquetas de estructura"
  - "etiquetas, etiquetas de estructura"
  - "union (palabra clave) [C]"
  - "union (palabra clave) [C], etiquetas"
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Espacios de nombres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador configura “espacios de nombres” para distinguir entre los identificadores utilizados para los diferentes tipos de elementos.  Los nombres de cada espacio de nombres deben ser únicos para evitar conflictos, pero un nombre idéntico puede aparecer en más de un espacio de nombres.  Esto significa que se puede utilizar el mismo identificador para dos o más elementos diferentes, siempre que los elementos estén en diferentes espacios de nombres.  El compilador puede resolver referencias en función del contexto sintáctico del identificador en el programa.  
  
> [!NOTE]
>  No confunda la noción limitada de C de un espacio de nombres con la característica “espacio de nombres” de C\+\+.  Vea [Espacios de nombres](../cpp/namespaces-cpp.md) en la Referencia del lenguaje C*\+\+* para obtener más información.  
  
 En esta lista se describen los espacios de nombres utilizados en C.  
  
 Etiquetas de instrucción  
 Las etiquetas de instrucción con nombre forman parte de instrucciones.  Las definiciones de las etiquetas de instrucción van seguidas siempre de un signo de dos puntos pero no siempre forman parte de las etiquetas **case**.  Los usos de etiquetas de instrucción siempre siguen inmediatamente a la palabra clave `goto`.  Las etiquetas de instrucción no tienen que ser distintas de otros nombres o de nombres de etiqueta de otras funciones.  
  
 Etiquetas de estructura, unión y enumeración  
 Estas etiquetas forman parte de los especificadores de tipo de estructura, unión y enumeración y, si están presentes, siempre siguen inmediatamente a palabras reservadas `struct`, **union** o `enum`.  Los nombres de etiqueta deben ser distintos del resto de las etiquetas de estructura, enumeración o unión con la misma visibilidad.  
  
 Miembros de estructuras o uniones  
 Los nombres de miembro se asignan en espacios de nombres asociados a cada tipo de estructura y unión.  Es decir, el mismo identificador puede ser un nombre de componente en cualquier número de estructuras o de uniones al mismo tiempo.  Las definiciones de nombres de componentes siempre aparecen dentro de especificadores de estructura o unión.  Los usos de nombres de componente siempre siguen inmediatamente a los operadores de selección de miembros \(**–\>** y **.**\).  El nombre de un miembro debe ser único dentro de la estructura o unión, pero no tiene que ser distinto de otros nombres del programa, incluidos los nombres de los miembros de diferentes estructuras y uniones o el nombre de la propia estructura.  
  
 Identificadores normales  
 El resto de los nombres caen dentro de un espacio de nombres que incluye variables, funciones \(incluyendo parámetros formales y variables locales\) y constantes de enumeración.  Los nombres de identificador tienen visibilidad anidada, por lo que puede volver a definirlos dentro de bloques.  
  
 Nombre de typedef  
 Los nombres de typedef no se pueden utilizar como identificadores en el mismo ámbito.  
  
 Por ejemplo, dado que las etiquetas de estructura, los miembros de estructura y los nombres de variable están en tres espacios de nombres diferentes, los tres elementos denominados `student` en este ejemplo no están en conflicto.  El contexto de cada elemento permite la interpretación correcta de cada aparición de `student` en el programa. \(Para obtener información sobre las estructuras, vea [Declaraciones de estructura](../c-language/structure-declarations.md).\)  
  
```  
struct student {  
   char student[20];  
   int class;  
   int id;  
   } student;  
```  
  
 Cuando `student` aparece después de la palabra clave `struct`, el compilador la reconoce como una etiqueta de estructura.  Cuando `student` aparece después de un operador de selección de miembros \(**–\>** o **.**\), el nombre hace referencia al miembro de estructura.  En otros contextos, `student` hace referencia a la variable de estructura.  Sin embargo, no se recomienda sobrecargar el espacio de nombres de etiqueta porque se oculta el significado.  
  
## Vea también  
 [Estructura del programa](../c-language/program-structure.md)