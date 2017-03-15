---
title: "Vinculaci&#243;n en nombres con &#225;mbito de archivo | Microsoft Docs"
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
  - "declaraciones [C++], externos"
  - "vinculación externa, reglas de vinculación de ámbito"
  - "ámbito de archivo [C++]"
  - "vinculación [C++], reglas de vinculación de ámbito"
  - "nombres [C++], reglas de vinculación de ámbito"
  - "ámbito [C++], reglas de vinculación"
  - "static (modificador), ámbito de archivo"
  - "nombres estáticos y ámbito de archivo"
  - "variables estáticas, declaraciones externas"
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Vinculaci&#243;n en nombres con &#225;mbito de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes reglas de vinculación se aplican a los nombres \(que no sean `typedef` y nombres de enumerador\) con ámbito de archivo:  
  
-   Si un nombre se declara explícitamente como **static**, tiene vinculación interna e identifica un elemento de programa dentro de su propia unidad de traducción.  
  
-   Los nombres de enumeradores y nombres `typedef` no tienen ninguna vinculación.  
  
-   El resto de los nombres con ámbito de archivo tienen vinculación externa.  
  
 **Específicos de Microsoft**  
  
-   Si un nombre de función con ámbito de archivo se declara explícitamente como **inline**, tiene una vinculación externa si se crean instancias del mismo o se hace referencia a su dirección.  Por consiguiente, es posible que una función con ámbito de archivo tenga vinculación interna o externa.  
  
 **FIN de Específicos de Microsoft**  
  
 Una clase tiene vinculación interna si:  
  
-   No utiliza ninguna funcionalidad de C\+\+ \(por ejemplo, control de acceso a miembros, funciones miembro, constructores, destructores, etc.\).  
  
-   No se utiliza en la declaración de otro nombre con vinculación externa.  Esta restricción significa que los objetos de tipo de clase que se pasan a funciones con vinculación externa hacen que la clase tenga vinculación externa.  
  
## Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)