---
title: "/SECTION (EDITBIN) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION (opción de editbin)"
  - "caracteres de alineación en secciones"
  - "SECTION (opción de editbin)"
  - "-SECTION (opción de editbin)"
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /SECTION (EDITBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## Comentarios  
 Esta opción modifica los atributos de una sección, pasando por alto los atributos establecidos cuando se compiló o vinculó el archivo objeto correspondiente a la sección.  
  
 Después de los dos puntos \( **:** \), especifique el valor de *name* correspondiente a la sección.  Para cambiar el nombre de la sección, escriba a continuación de *name* un signo igual \(\=\) y un valor de *newname* para la sección.  
  
 Para establecer o cambiar los valores de `attributes` correspondientes a la sección, especifique una coma \(**,**\) seguida por uno o más caracteres de atributo.  Para negar un atributo, su carácter deberá ir precedido por un signo de admiración \(\!\).  Los siguientes caracteres especifican atributos de memoria:  
  
|Atributo|Opción de configuración|  
|--------------|-----------------------------|  
|c|code|  
|d|descartable|  
|e|ejecutable|  
|i|datos inicializados|  
|k|memoria virtual almacenada en caché|  
|m|eliminación de vínculo|  
|o|información de vínculo|  
|p|memoria virtual paginada|  
|r|lectura|  
|s|compartido|  
|u|datos no inicializados|  
|w|escritura|  
  
 Para controlar el valor de *alignment*, especifique el carácter **A** seguido de uno de los siguientes caracteres para establecer el tamaño de alineación en bytes, tal y como se indica a continuación:  
  
|Carácter|Tamaño de alineación en bytes|  
|--------------|-----------------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|s|64|  
|x|sin alineación|  
  
 Especifique los caracteres de `attributes` y *alignment* como una cadena sin espacios en blanco.  Para estos caracteres, no se distingue mayúsculas de minúsculas.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)